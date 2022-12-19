<template>

  <fieldset class="fieldset">
    <legend>Incident Type</legend>
    <span><input type="checkbox" value="100,110,120" v-model="incident_type"><label>Homicide</label></span>
    <span><input type="checkbox" value="210,220" v-model="incident_type"><label>Rape</label></span>
    <span>
            <input
                type="checkbox"
                value="300,311,312,313,314,321,322,323,324,331,333,334,341,342,343,344,351,352,353,354,361,363,364,371,372,373,374"
                v-model="incident_type">
            <label>Robbery</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="400,410,411,412,420,421,422,430,431,432,440,441,442,450,451,452,453"
                v-model="incident_type">
            <label>Aggravated Assault</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="500,510,511,513,515,516,520,521,523,525,526,530,531,533,535,536,540,541,543,545,546,550,551,553,555,556,560,561,563,565,566"
                v-model="incident_type">
            <label>Burglary</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="600,603,611,612,613,614,621,622,623,630,631,632,633,640,641,642,643,651,652,653,661,662,663,671,672,673,681,682,683,691,692,693"
                v-model="incident_type">
            <label>Theft</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="700,710,711,712,720,721,722,730,731,732"
                v-model="incident_type">
            <label>Motor Vehicle Theft</label>
        </span>
    <span>
            <input type="checkbox" value="810,861,862,863" v-model="incident_type">
            <label>Asasult</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="900,901,903,905,911,913,915,921,922,923,925,931,933,941,942,951,961,971,972,975,981,982"
                v-model="incident_type">
            <label>Arson</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="1400,1401,1410,1415,1416,1420,1425,1426,1430,1435,1436"
                v-model="incident_type">
            <label>Criminal Damage to Property</label>
        </span>
    <span>
            <input
                type="checkbox"
                value="1800,1810,1811,1812,1813,1814,1815,1820,1822,1823,1824,1825,1830,1835,1840,1841,1842,1843,1844,1845,1850,1855,1860,1865,1870,1880,1885"
                v-model="incident_type">
            <label>Narcotics</label>
        </span>
    <span><input type="checkbox" value="2619" v-model="incident_type"><label>Weapons</label></span>
    <span><input type="checkbox" value="3100"
                 v-model="incident_type"><label>Death-Investigation of A Death</label></span>
    <span><input type="checkbox" value="9954,9959,9986"
                 v-model="incident_type"><label>Proactive Police Visit</label></span>
  </fieldset>

  <fieldset class="fieldset">
    <legend>Neighborhood Names</legend>
    <span><input type="checkbox" value="1"
                 v-model="neighborhood_number"><label>Conway/Battlecreek/Highwood</label></span>
    <span><input type="checkbox" value="2" v-model="neighborhood_number"><label>Greater East Side</label></span>
    <span><input type="checkbox" value="3" v-model="neighborhood_number"><label>West Side</label></span>
    <span><input type="checkbox" value="4" v-model="neighborhood_number"><label>Dayton's Bluff</label></span>
    <span><input type="checkbox" value="5" v-model="neighborhood_number"><label>Payne/Phalen</label></span>
    <span><input type="checkbox" value="6" v-model="neighborhood_number"><label>North End</label></span>
    <span><input type="checkbox" value="7" v-model="neighborhood_number"><label>Thomas/Dale(Frogtown)</label></span>
    <span><input type="checkbox" value="8" v-model="neighborhood_number"><label>Summit/University</label></span>
    <span><input type="checkbox" value="9" v-model="neighborhood_number"><label>West Seventh</label></span>
    <span><input type="checkbox" value="10" v-model="neighborhood_number"><label>Como</label></span>
    <span><input type="checkbox" value="11" v-model="neighborhood_number"><label>Hamline/Midway</label></span>
    <span><input type="checkbox" value="12" v-model="neighborhood_number"><label>St. Anthony</label></span>
    <span><input type="checkbox" value="13" v-model="neighborhood_number"><label>Union Park</label></span>
    <span><input type="checkbox" value="14" v-model="neighborhood_number"><label>Macalester-Groveland</label></span>
    <span><input type="checkbox" value="15" v-model="neighborhood_number"><label>Highland</label></span>
    <span><input type="checkbox" value="16" v-model="neighborhood_number"><label>Summit Hill</label></span>
    <span><input type="checkbox" value="17" v-model="neighborhood_number"><label>Capitol River</label></span>
  </fieldset>

  <fieldset class="fieldset">
    <legend>Date Range</legend>
    <div class="grid-x">
      <div class="cell medium-6 date">
        <label>Start Date</label><input type="date" v-model="start_date"/>
      </div>
      <div class="cell medium-6 date">
        <label>End Date</label><input type="date" v-model="end_date"/>
      </div>
    </div>
  </fieldset>

  <fieldset class="fieldset">
    <legend>Time Range</legend>
    <div class="grid-x">
      <div class="cell medium-6 time">
        <label>Start Time</label><input type="time" step="2" v-model="start_time"/>
      </div>
      <div class="cell medium-6 time">
        <label>End Time</label><input type="time" step="2" v-model="end_time"/>
      </div>
    </div>
  </fieldset>

  <fieldset class="fieldset">
    <legend>Max Incidents</legend>
    <div class="grid-x">
      <div class="cell medium-6 limit">
        <label>Limit</label><input type="text" v-model="limit">
      </div>
    </div>
  </fieldset>

  <button class="button" @click="getData">Update</button>

  <div>
  <ul class="legend">
    <li><span class="red"></span> Violent Crimes</li>
    <li><span class="yellow"></span> Property Crimes</li>
    <li><span class="blue"></span> Other Crimes</li>
  </ul>
  </div>
  <table>
    <thead>
    <th>Case Number</th>
    <th>Incident Type</th>
    <th>Incident</th>
    <th>Police Grid</th>
    <th>Neighborhood Name</th>
    <th>Block</th>
    <th>Date</th>
    <th>Time</th>
    <th>Delete</th>
    </thead>
    <tbody v-for="(item) in computedData">


    <tr v-if="([300,311,312,313,314,321,322,323,324,331,333,334,341,342,343,344,351,352,353,354,361,363,364,371,372,373,374,
        500,510,511,513,515,516,520,521,523,525,526,530,531,533,535,536,540,541,543,545,546,550,551,553,555,556,560,561,563,565,566,
        600,603,611,612,613,614,621,622,623,630,631,632,633,640,641,642,643,651,652,653,661,662,663,671,672,673,681,682,683,691,692,693,
        700,710,711,712,720,721,722,730,731,732,1400,1401,1410,1415,1416,1420,1425,1426,1430,1435,1436].indexOf(item.code) > -1)"
        class="yellow" @click="placeMarker(item.date,item.time,item.incident, item.block, item.case_number)">
      <td>{{ item.case_number }}</td>
      <td>{{ item.incident_type }}</td>
      <td>{{ item.incident }}</td>
      <td>{{ item.police_grid }}</td>
      <td>{{ item.neighborhood_name }}</td>
      <td>{{ item.block }}</td>
      <td>{{ item.date }}</td>
      <td>{{ item.time }}</td>
      <td><button @click = "deleteItem(item)" class="button">DELETE</button></td>
    </tr>
      <tr v-else-if="([400,410,411,412,420,421,422,430,431,432,440,441,442,450,451,452,453,810,861,862,863].indexOf(item.code) > -1)"
          class="red" @click="placeMarker(item.date,item.time,item.incident, item.block, item.case_number)">
      <td>{{ item.case_number }}</td>
      <td>{{ item.incident_type }}</td>
      <td>{{ item.incident }}</td>
      <td>{{ item.police_grid }}</td>
      <td>{{ item.neighborhood_name }}</td>
      <td>{{ item.block }}</td>
      <td>{{ item.date }}</td>
      <td>{{ item.time }}</td>
        <td><button @click = "deleteItem(item)" class="button">DELETE</button></td>
    </tr>
      <tr v-else class="blue" @click="placeMarker(item.date,item.time,item.incident, item.block, item.case_number)">
      <td>{{ item.case_number }}</td>
      <td>{{ item.incident_type }}</td>
      <td>{{ item.incident }}</td>
      <td>{{ item.police_grid }}</td>
      <td>{{ item.neighborhood_name }}</td>
      <td>{{ item.block }}</td>
      <td>{{ item.date }}</td>
      <td>{{ item.time }}</td>
        <td><button @click = "deleteItem(item)" class="button">DELETE</button></td>
    </tr>


    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    uploadMethod: Function,
    getJson: Function,
    leaflet: Object
  },

  beforeMount() {
    this.getData();
    this.getJson("http://localhost:8000/neighborhoods").then((res2) => {
      this.data.map(r => {
        let n_item = res2.find(r2 => r.neighborhood_number === r2.neighborhood_number);
        r.neighborhood_name = n_item ? n_item.neighborhood_name : null;
        return r;
      })
    })
    this.getJson("http://localhost:8000/codes")
        .then((res) => {
          this.data.map(r1 => {
            let c_item = res.find(r3 => r1.code === r3.code);
            r1.incident_type = c_item ? c_item.incident_type : null;
            return r1;
          })
        });
  },

  data() {
    return {
      data: [],
      incident_type: [],
      neighborhood_number: [],
      start_date: "",
      end_date: "",
      start_time: "",
      end_time: "",
      limit: "",
      selectedIncident: "",
      neighborhood_data: [],
      incident_type_data: []
    }
  },

  computed: {
    code() {
      let codes = "";
      for (let i = 0; i < this.incident_type.length; i++) {
        codes += this.incident_type[i] + ",";
      }
      codes = codes.substring(0, codes.length - 1);
      return codes;
    },

    neighborhood_numbers() {
      let numbers = "";
      for (let i = 0; i < this.neighborhood_number.length; i++) {
        numbers += this.neighborhood_number[i] + ",";
      }
      numbers = numbers.substring(0, numbers.length - 1);
      return numbers;
    },

    query() {
      let query = "http://localhost:8000/incidents";
      let clause = "?"

      if (this.incident_type.length > 0) {
        query += clause + "code=" + this.code;
        clause = "&";
      }

      if (this.neighborhood_number.length > 0) {
        query += clause + "neighborhood_number=" + this.neighborhood_numbers;
        clause = "&";
      }

      if (this.start_date !== "") {
        query += clause + "start_date=" + this.start_date;
        clause = "&";
      }

      if (this.end_date !== "") {
        query += clause + "end_date=" + this.end_date;
        clause = "&";
      }

      if (this.start_time !== "") {
        query += clause + "start_time=" + this.start_time;
        clause = "&";
      }

      if (this.end_time !== "") {
        query += clause + "end_time=" + this.end_time;
        clause = "&";
      }

      if (this.limit !== "") {
        query += clause + "limit=" + this.limit;
        clause = "&";
      }

      return query;
    },

    computedData() {
      let newData = [];
      for (let i=0; i<this.data.length; i++) {
        let incidentLocation = this.niceLocation(this.data[i].block);
        this.getJson('https://nominatim.openstreetmap.org/search?q=' + incidentLocation + '&format=json&limit=25&accept-language=en')
        .then((res)=>{
          let lat = res[0].lat;
          let lng = res[0].lng;
          if (lat < this.leaflet.currentBounds.northEast.lat && lat > this.leaflet.currentBounds.southWest.lat) {
            if (lng < this.leaflet.currentBounds.northEast.lng && lng > this.leaflet.currentBounds.southWest.lng) {
              newData.push(this.data[i]);
            }
          }
        })
      }
      return newData;
    }
  },

  methods: {
    getData() {
      this.getJson(this.query)
          .then((res) => {
            this.data = res;
          })
          .catch((err) => {

          })
    },

    niceLocation(location) {
      let locationSplit = location.split(" ");
      if(locationSplit[0].includes("X") || locationSplit[0].includes('x')){
        let alteredAddress = locationSplit[0].replaceAll("X","0");
        alteredAddress = alteredAddress.replaceAll('x','0');
        locationSplit[0] = alteredAddress;
      }

      let fullAddress = '';
      for(let i =0; i<locationSplit.length;i++){
        fullAddress += locationSplit[i] + ' ';
      }
      fullAddress += ', St.Paul, MN';
      return fullAddress;
    },

    placeMarker(date, time, incident, location, case_number){
      $(".leaflet-marker-icon").remove(); $(".leaflet-popup").remove();
      $(".leaflet-pane.leaflet-shadow-pane").remove();
      console.log(date);
      console.log(time);
      console.log(incident);

      let locationSplit = location.split(" ");
      if(locationSplit[0].includes("X") || locationSplit[0].includes('x')){
        let alteredAddress = locationSplit[0].replaceAll("X","0");
        alteredAddress = alteredAddress.replaceAll('x','0');
        locationSplit[0] = alteredAddress;
      }

      let fullAddress = '';
      for(let i =0; i<locationSplit.length;i++){
        fullAddress += locationSplit[i] + ' ';
      }
      fullAddress += ', St.Paul, MN'


      this.getJson('https://nominatim.openstreetmap.org/search?q=' + fullAddress + '&format=json&limit=25&accept-language=en').then((result) => {
                    //console.log(result);
                    if(result.length === 0){
                      alert("This row is invalid\nPlease try again.");
                      return;
                    }
                    let latitude = Number(result[0].lat);
                    let longitude = Number(result[0].lon);
                    if(latitude < 44.8883383134382 || latitude > 44.99159144730164){
                        alert("This row is invalid");
                        return;
                    }

                    if(longitude < -93.20744225904383 || longitude > -93.0043790042584){
                        alert("This row is invalid");
                        return;
                    }

                    let leafletIcon = L.icon({
                      iconUrl: '/imgs/crimeIcon.png',
                      iconSize:[38,45],
                      iconAnchor:[20,75],
                      popupAnchor: [0,-80]
                    })


                    L.marker([latitude,longitude],{icon: leafletIcon}).addTo(this.leaflet.map)
                  .bindPopup('Date: ' + date  + '<br>Time: ' + time  + '<br>Incident: ' + incident + '<br><br><center><button @click="removeMarkers" type = "button" class = "button" id ="popupButton"> Delete Incident </button>')
                  .openPopup();
                  L.DomEvent.on(popupButton, 'click', () => {
                    this.removeMarkers(case_number);
                  });

                });

    },
    removeMarkers(case_number){
      $(".leaflet-marker-icon").remove(); $(".leaflet-popup").remove();
      $(".leaflet-pane.leaflet-shadow-pane").remove();
      console.log('HELLO')
      alert('Incident #' + String(case_number) + ' has been deleted')
    },
    checkIncidentType(item) {
      if([300,311,312,313,314,321,322,323,324,331,333,334,341,342,343,344,351,352,353,354,361,363,364,371,372,373,374,
        500,510,511,513,515,516,520,521,523,525,526,530,531,533,535,536,540,541,543,545,546,550,551,553,555,556,560,561,563,565,566,
        600,603,611,612,613,614,621,622,623,630,631,632,633,640,641,642,643,651,652,653,661,662,663,671,672,673,681,682,683,691,692,693,
        700,710,711,712,720,721,722,730,731,732,1400,1401,1410,1415,1416,1420,1425,1426,1430,1435,1436].indexOf(item.code) > -1) {
        return "yellow";
      } else if([400,410,411,412,420,421,422,430,431,432,440,441,442,450,451,452,453,810,861,862,863].indexOf(item.code) > -1) {
        return "red";
      } else {
        return "blue";
      }
    },
    deleteItem(item) {
      this.uploadMethod("DELETE", "http://localhost:8000/remove-incident", item)
          .then((res) => {
            window.location.reload();
            window.alert("removed incident successfully");
          })
          .catch((err) => {
            console.log("There's an error!");
            window.alert("Something went wrong!");
          })
    }
  }
}

</script>

<style>
.fieldset {
  width: 100%;
}

.fieldset span {
  display: block;
  float: left;
}

.date input, .time input, .limit input {
  width: 75%;
}

.red {
  background-color: #ff8a8a;
}

.yellow {
  background-color: #ffff9f;
}

.blue {
  background-color: #89cff0;
}

.legend { list-style: none; }
.legend li { float: left; margin-right: 10px; }
.legend span { border: 1px solid #ccc; float: left; width: 12px; height: 12px; margin: 2px; }

</style>