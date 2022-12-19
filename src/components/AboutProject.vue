<template>
    <h2>Team Members</h2>
    <div class="grid-x">
        <div class="cell small-12 medium-4">
            <img src="../images/tina.jpg" alt="Tina Portrait">
        </div>
        <div class="cell small-12 medium-8">
            <h4>Tina Trinh</h4>
            <p>
                Current senior, major in Computer Science with minors in Data Analytics and Applied Statistics.
                I'm from Ho Chi Minh, Vietnam. My hobby is singing, dancing, and listening to music.
            </p>
        </div>
    </div>

    <div class="grid-x">
        <div class="cell small-12 medium-4">
            <img src="../images/aashish.jpg" alt="Aashish Portrait">
        </div>
        <div class="cell small-12 medium-8">
            <h4>Aashish Bharath</h4>
            <p>
                My name is Aashish Bharath, and I am a senior at University of St. Thomas.
                I am majoring in Data Analytics and Economics with a minor in Computer Science.
                After my graduation in the spring of 2023, I will be working as a Analytics and Data Science ADP at Trane Technologies.
                In my free time I enjoy hiking, photography, watching movies, and spending time with friends and family.
            </p>
        </div>
    </div>

    <div class="grid-x">
        <div class="cell small-12 medium-4">
            <img src="../images/sunisha.jpg" alt="Sunisha Portrait">
        </div>
        <div class="cell small-12 medium-8">
            <h4>Sunisha Arora</h4>
            <p>
                Name: Sunisha Arora <br>
                Year: Senior <br>
                Major: Computer Science and Data Analytics (Economics) <br>
                Hometown: Bhopal, India <br>
            </p>
        </div>
    </div>

    <h2>Tools/Frameworks</h2>
    <p>
        To create this website we used a few tools to make development smoother.
        These tools included frameworks like Foundation for CSS and Vue.js to easily build the user interface and our single page web application.
    </p>
    <h4>Project 3 RESTful Server, Leaflet, and Nominatim API</h4>
    <p>
        We also used a couple APIs to gather, and visualize the St. Paul Crime Data.
        First, our data comes from a RESTful API that we built previously.
        To visualize the incident data we use the Leaflet API to easily visualize crime incidents on a map.
        And finally we used the Nominatim API which smoothly converts between address and latitude/longitude.
    </p>
    <h4>Vue.js</h4>
    <p>
        We used Vue.js framework to manage our front-end app structure and logic.
        Vue.js allowed us to manage and update app state efficiently through data binding and lifecycle hooks.
    </p>

    <h2>Video Demo</h2>

    <h2>Interesting Things We Learned</h2>
    <ol>
        <li>
            There are 151 rape incidents from 12 PM - 3 PM, 154 rape incidents  from 9 PM - midnight, and 146 rape incidents from midnight - 3 AM.
            The number of rape incidents are surprisingly similar at these 3-hour time ranges of the day.
        </li>
        <li>
            The number of robbery incidents that happen at from 9 PM - midnight (855 incidents) are about the same as the number of
            roberry incidents from 8 AM - 4 PM during the day.
        </li>
        <li>
            Burglary incidents happened the most at Payne/Phalen neighborhood with 2201 incidents,
            while there're only 500 burglary incidents at Capital River neighborhood.
        </li>
        <li>
            Most incidents occurring around campus (Summit/University) are property crimes (usually theft).
            There are very few violent crimes in the area (fortunately).
        </li>
        <li>
            Auto Theft Incident are very common in the Summit/University neighborhoods.
            From March 2022 to May 2022 there were over a 1000 incidents. This is more than 10 incidents a day.
        </li>
        <li>
            The highest cause of assault is domestic assault. On average, there are about 5 or 6 assault cases every day.
        </li>
    </ol>
</template>

<style>
    .grid-x {
        padding-bottom: 2rem;
    }
</style>