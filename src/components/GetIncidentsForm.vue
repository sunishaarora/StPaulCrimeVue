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
        <span><input type="checkbox" value="3100" v-model="incident_type"><label>Death-Investigation of A Death</label></span>
        <span><input type="checkbox" value="9954,9959,9986" v-model="incident_type"><label>Proactive Police Visit</label></span>
    </fieldset>

    <fieldset class="fieldset">
        <legend>Neighborhood Names</legend>
        <span><input type="checkbox" value="1" v-model="neighborhood_number"><label>Conway/Battlecreek/Highwood</label></span>
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

    <button class="button">Update</button>
</template>

<script>
    export default {
        data() {
            return {
                incident_type: [],
                neighborhood_number: [],
                start_date: "",
                end_date: "",
                start_time: "",
                end_time: "",
                limit: 1000
            }
        },

        computed: {
            code() {
                let codes = "";
                for (let i=0; i<this.incident_type.length; i++) {
                    codes += this.incident_type[i] + ",";
                }
                codes = codes.substring(0, codes.length-1);
                return codes;
            },

            neighborhood_numbers() {
                let numbers = "";
                for (let i=0; i<this.neighborhood_number.length; i++) {
                    numbers += this.neighborhood_number[i] + ",";
                }
                numbers = numbers.substring(0, numbers.length-1);
                return numbers;
            },

            start_date_time() {
                return this.start_date + "T" + this.start_time;
            },

            end_date_time() {
                return this.end_date + "T" + this.end_time;
            },

            query() {
                let query = "";
                let clause = "?"

                if (this.incident_type.length > 0) {
                    query += clause + "code=" + this.code;
                    clause = "&";
                }

                if (this.neighborhood_number.length > 0) {
                    query += clause + "neighborhood_number=" + this.neighborhood_numbers;
                    clause = "&";
                }

                return query;
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
</style>