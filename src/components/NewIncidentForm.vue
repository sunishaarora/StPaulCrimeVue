<template>
    <div class="form">
        <label>
            Case Number
            <input type="text" v-model="data.case_number" placeholder="Enter case number"/>
        </label>

        <label>
            Date
            <input type="date" v-model="data.date"/>
        </label>

        <label>
            Time
            <input type="time" step="2" v-model="data.time">
        </label>

        <label>
            Code
            <input type="text" v-model="data.code" placeholder="Enter code"/>
        </label>

        <label>
            Incident
            <input type="text" v-model="data.incident" placeholder="Enter incident description">
        </label>

        <label>
            Police Grid
            <input type="text" v-model="data.police_grid" placeholder="Enter police grid">
        </label>

        <label>
            Neighborhood Number
            <input type="text" v-model="data.neighborhood_number" placeholder="Enter neighborhood number">
        </label>

        <label>
            Block
            <input type="text" v-model="data.block" placeholder="Enter block name">
        </label>

        <input type="submit" class="button" value="Submit" @click="submitForm">
    </div>
</template>

<script>
    import $ from 'jquery'

    export default {
        props: {
            uploadMethod: Function
        },

        data() {
            return {
                data: {
                    case_number: "",
                    date: "",
                    time: "",
                    code: "",
                    incident: "",
                    police_grid: "",
                    neighborhood_number: "",
                    block: ""
                }
            }
        },

        methods: {
            submitForm() {
                if (this.data.case_number == "" || this.data.date == "" || this.data.time == "" || this.data.code == "" || this.data.incident == "" || this.data.police_grid == "" || this.data.neighborhood_number == "" || this.data.block == "") {
                    window.alert("Please fill out all fields in the form");
                } else {
                    this.uploadMethod("PUT", "http://localhost:8000/new-incident", this.data)
                    .then((res)=>{
                        window.alert(res);
                    })
                    .catch((err)=>{
                        window.alert(err.message);
                    })
                }
            }
        }
    }
</script>

<style>
    .form {
        width: 40%;
    }
</style>