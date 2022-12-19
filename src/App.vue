<script>
import $ from 'jquery'
import NewIncidentFormVue from './components/NewIncidentForm.vue';
import GetIncidentsFormVue from './components/GetIncidentsForm.vue';
//import SearchResult from './components/SearchResult.vue'
export default {
    components: {
        NewIncidentFormVue,
        GetIncidentsFormVue
    },
    data() {
        return {
            view: 'map',
            userSearch: '44.955139, -93.102222 ',
            userLat:44.949203,
            userLng: -93.093739,
            codes: [],
            neighborhoods: [],
            incidents: [],
            leaflet: {
                map: null,
                center: {
                    lat: 44.955139,
                    lng: -93.102222,
                    address: ""
                },
                zoom: 12,
                bounds: {
                    nw: {lat: 45.008206, lng: -93.217977},
                    se: {lat: 44.883658, lng: -92.993787}
                },
                neighborhood_markers: [
                    {location: [44.942068, -93.020521], marker: null},
                    {location: [44.977413, -93.025156], marker: null},
                    {location: [44.931244, -93.079578], marker: null},
                    {location: [44.956192, -93.060189], marker: null},
                    {location: [44.978883, -93.068163], marker: null},
                    {location: [44.975766, -93.113887], marker: null},
                    {location: [44.959639, -93.121271], marker: null},
                    {location: [44.947700, -93.128505], marker: null},
                    {location: [44.930276, -93.119911], marker: null},
                    {location: [44.982752, -93.147910], marker: null},
                    {location: [44.963631, -93.167548], marker: null},
                    {location: [44.973971, -93.197965], marker: null},
                    {location: [44.949043, -93.178261], marker: null},
                    {location: [44.934848, -93.176736], marker: null},
                    {location: [44.913106, -93.170779], marker: null},
                    {location: [44.937705, -93.136997], marker: null},
                    {location: [44.949203, -93.093739], marker: null}
                ],
                currentBounds: {
                    northEast: {
                        lat: 0,
                        lng: 0
                    },
                    southWest: {
                        lat: 0,
                        lng: 0,
                    }
                }

            }
        };
    },
    methods: {
        viewMap(event) {
            this.view = 'map';
        },
        viewNewIncident(event) {
            this.view = 'new_incident';
        },
        viewAbout(event) {
            this.view = 'about';
        },
        getJSON(url) {
            return new Promise((resolve, reject) => {
                $.ajax({
                    dataType: 'json',
                    url: url,
                    success: (response) => {
                        resolve(response);
                    },
                    error: (status, message) => {
                        reject({status: status.status, message: status.statusText});
                    }
                });
            });
        },
        uploadJSON(method, url, data) {
            return new Promise((resolve, reject) => {
                $.ajax({
                    type: method,
                    url: url,
                    contentType: 'application/json; charset=utf-8',
                    data: JSON.stringify(data),
                    dataType: 'text',
                    success: (response) => {
                        resolve(response);
                    },
                    error: (status, message) => {
                        reject({status: status.status, message: status.statusText});
                    }
                });
            });
        },
        enter(){
            $(".leaflet-marker-icon").remove(); $(".leaflet-popup").remove();
            $(".leaflet-pane.leaflet-shadow-pane").remove();
            console.log(this.userSearch);
            //this.leaflet.map.setView(latlng)
            var searchResult = this.userSearch;
            let newLat = 0;
            let newLng = 0;
            var latlng_obj;
            console.log('nominatim api: ' + 'https://nominatim.openstreetmap.org/search?q=' + searchResult + '&format=json&limit=25&accept-language=en');
            this.getJSON('https://nominatim.openstreetmap.org/search?q=' + searchResult + '&format=json&limit=25&accept-language=en').then((result) => {
                // St. Paul GeoJSON
                //console.log(result);
                this.userLat = Number(result[0].lat);
                this.userLng = Number(result[0].lon);
                newLat = this.userLat;
                newLng = this.userLng;
                if(newLat > 45.008206 || newLat < 44.883658){
                    console.log('Address is not within bounds')
                    var popup = L.popup().setLatLng(this.leaflet.center).setContent('Address is not within bounds').openOn(this.leaflet.map);
                }else if(newLng > -92.993787 || newLng < -93.217977){
                    console.log('Address is not within bounds')
                    var popup = L.popup().setLatLng(this.leaflet.center).setContent('Address is not within bounds').openOn(this.leaflet.map);
                }else{
                    var popup = L.popup().setLatLng([newLat, newLng]).setContent(result[0]['display_name']).openOn(this.leaflet.map);
                    this.leaflet.map.panTo([newLat,newLng]);
                }
            }).catch((error) => {
                console.log('Error:', error);
                var popup = L.popup().setLatLng(this.leaflet.center).setContent('Error. Please try again.').openOn(this.leaflet.map);
            });
        },
        mouseClick(){
            function getJSON(url) {
                return new Promise((resolve, reject) => {
                    $.ajax({
                        dataType: 'json',
                        url: url,
                        success: (response) => {
                            resolve(response);
                        },
                        error: (status, message) => {
                            reject({status: status.status, message: status.statusText});
                        }
                    });
                });
            }
            function getAddress(search){
                getJSON('https://nominatim.openstreetmap.org/search?q=' + search + '&format=json&limit=25&accept-language=en').then((result) => {
                    console.log(this.leaflet.center);
                    L.popup().setLatLng([result[0].lat,result[0].lon]).setContent(result[0]['display_name']).openOn(this.leaflet.map);
                });
            }
            this.leaflet.map.on('click', function(ev) {
                var clickLat = String(ev.latlng.lat);
                var clickLng = String(ev.latlng.lat);
                var searchResult = clickLat + "," + clickLng;
                getAddress(searchResult, ev.latlng);
            });
        },
        load(event){
            let current_latLon = String(this.leaflet.map.getCenter().lat) +','+String(this.leaflet.map.getCenter().lng);
            this.getJSON('https://nominatim.openstreetmap.org/search?q=' + current_latLon + '&format=json&limit=25&accept-language=en').then((result) => {
                    console.log(this.leaflet.center);
                    this.userSearch = result[0]['display_name']
                });

        },
        onMoveEnd(event){
            let current_latLon = String(this.leaflet.map.getCenter().lat) +','+String(this.leaflet.map.getCenter().lng);
            this.getJSON('https://nominatim.openstreetmap.org/search?q=' + current_latLon + '&format=json&limit=25&accept-language=en').then((result) => {
                    console.log(this.leaflet.center);
                    this.userSearch = result[0]['display_name']
                });

            console.log("New bounds: ", this.leaflet.map.getBounds());
            let newBounds = this.leaflet.map.getBounds();
            console.log(newBounds._northEast.lat);
            this.leaflet.currentBounds.northEast.lat = newBounds._northEast.lat;
            this.leaflet.currentBounds.northEast.lng = newBounds._northEast.lng;
            this.leaflet.currentBounds.southWest.lat = newBounds._southWest.lat;
            this.leaflet.currentBounds.southWest.lng = newBounds._southWest.lng;
        }
    },
    mounted() {
        this.leaflet.map = L.map('leafletmap').setView([this.leaflet.center.lat, this.leaflet.center.lng], this.leaflet.zoom);
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
            minZoom: 11,
            maxZoom: 18
        }).addTo(this.leaflet.map);
        this.leaflet.map.setMaxBounds([[44.883658, -93.217977], [45.008206, -92.993787]]);

        this.leaflet.map.on('load', this.OnLoad);
        this.leaflet.map.on('moveend', this.onMoveEnd);

        let district_boundary = new L.geoJson();
        district_boundary.addTo(this.leaflet.map);
        this.getJSON('/data/StPaulDistrictCouncil.geojson').then((result) => {
            // St. Paul GeoJSON
            $(result.features).each((key, value) => {
                district_boundary.addData(value);
            });
        }).catch((error) => {
            console.log('Error:', error);
        });

      // this.$root.$on('GetIncidentsForm', () => {
      //   this.c1method();
      // })
    }
}
</script>

<template>
    <div class="grid-container">
        <div class="grid-x grid-padding-x">
            <p :class="'cell small-4 ' + ((view === 'map') ? 'selected' : 'unselected')" @click="viewMap">Map</p>
            <p :class="'cell small-4 ' + ((view === 'new_incident') ? 'selected' : 'unselected')" @click="viewNewIncident">New Incident</p>
            <p :class="'cell small-4 ' + ((view === 'about') ? 'selected' : 'unselected')" @click="viewAbout">About</p>
        </div>
    </div>
    <div v-show="view === 'map'">
        <div class="grid-container">
            <br />
            <input style = 'width: 800px;' id = 'InputID' v-model = "userSearch" placeholder="Search Here" />
            <button onclick="document.getElementById('InputID').value = ''" type = 'button' class = 'button' @click="enter" @keyup.enter="enter"> Go</button>


            <div class="grid-x grid-padding-x">
                <div @click="mouseClick" id="leafletmap" class="cell auto"></div>
            </div>

            <div class="grid-x grid-padding-x">
                <GetIncidentsFormVue :getJson="getJSON" , :leaflet = "leaflet" />
            </div>
        </div>
    </div>
    <div v-if="view === 'new_incident'">
        <!-- Replace this with your actual form: can be done here or by making a new component -->
        <div class="grid-container">
            <div class="grid-x grid-padding-x">
                <h1 class="cell auto">New Incident Form</h1>
            </div>
            <div class="grid-x">
                <NewIncidentFormVue :uploadMethod="uploadJSON" />
            </div>
        </div>
    </div>
    <div v-if="view === 'about'">
        <!-- Replace this with your actual about the project content: can be done here or by making a new component -->
        <div class="grid-container">
            <div class="grid-x grid-padding-x">
                <h1 class="cell auto">About the Project</h1>
            </div>
        </div>
    </div>
</template>

<style>
#leafletmap {
    height: 500px;
}
.selected {
    background-color: rgb(10, 100, 126);
    color: white;
    border: solid 1px white;
    text-align: center;
    cursor: pointer;
}
.unselected {
    background-color: rgb(200, 200, 200);
    color: black;
    border: solid 1px white;
    text-align: center;
    cursor: pointer;
}
</style>