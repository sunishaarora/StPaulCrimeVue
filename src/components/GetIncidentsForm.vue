<template>
    <fieldset class="fieldset">
        <legend>Incident Type</legend>
        <span><input type="checkbox"><label>Homicide</label></span>
        <span><input type="checkbox"><label>Rape</label></span>
        <span><input type="checkbox"><label>Robbery</label></span>
        <span><input type="checkbox"><label>Aggravated Assault</label></span>
        <span><input type="checkbox"><label>Burglary</label></span>
        <span><input type="checkbox"><label>Theft</label></span>
        <span><input type="checkbox"><label>Motor Vehicle Theft</label></span>
        <span><input type="checkbox"><label>Asasult</label></span>
        <span><input type="checkbox"><label>Arson</label></span>
        <span><input type="checkbox"><label>Criminal Damage to Property</label></span>
        <span><input type="checkbox"><label>Narcotics</label></span>
        <span><input type="checkbox"><label>Weapons</label></span>
        <span><input type="checkbox"><label>Death-Investigation of A Death</label></span>
        <span><input type="checkbox"><label>Proactive Police Visit</label></span>
    </fieldset>

    <fieldset class="fieldset">
        <legend>Neighborhood Names</legend>
        <span><input type="checkbox"><label>Conway/Battlecreek/Highwood</label></span>
        <span><input type="checkbox"><label>Greater East Side</label></span>
        <span><input type="checkbox"><label>West Side</label></span>
        <span><input type="checkbox"><label>Dayton's Bluff</label></span>
        <span><input type="checkbox"><label>Payne/Phalen</label></span>
        <span><input type="checkbox"><label>North End</label></span>
        <span><input type="checkbox"><label>Thomas/Dale(Frogtown)</label></span>
        <span><input type="checkbox"><label>Summit/University</label></span>
        <span><input type="checkbox"><label>West Seventh</label></span>
        <span><input type="checkbox"><label>Como</label></span>
        <span><input type="checkbox"><label>Hamline/Midway</label></span>
        <span><input type="checkbox"><label>St. Anthony</label></span>
        <span><input type="checkbox"><label>Union Park</label></span>
        <span><input type="checkbox"><label>Macalester-Groveland</label></span>
        <span><input type="checkbox"><label>Highland</label></span>
        <span><input type="checkbox"><label>Summit Hill</label></span>
        <span><input type="checkbox"><label>Capitol River</label></span>
    </fieldset>

    <fieldset class="fieldset">
        <legend>Date Range</legend>
        <div class="grid-x">
            <div class="cell medium-6 date">
                <label>Start Date</label><input type="date"/>
            </div>
            <div class="cell medium-6 date">
                <label>End Date</label><input type="date"/>
            </div>
        </div>
    </fieldset>

    <fieldset class="fieldset">
        <legend>Time Range</legend>
        <div class="grid-x">
            <div class="cell medium-6 time">
                <label>Start Time</label><input type="time" step="2"/>
            </div>
            <div class="cell medium-6 time">
                <label>End Time</label><input type="time" step="2"/>
            </div>
        </div>
    </fieldset>

    <fieldset class="fieldset">
        <legend>Max Incidents</legend>
        <div class="grid-x">
            <div class="cell medium-6 limit">
                <label>Limit</label><input type="text">
            </div>
        </div>
    </fieldset>

    <button class="button">Update</button>
</template>

<script>
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