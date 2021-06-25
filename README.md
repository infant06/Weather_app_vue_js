<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="Weather_App_by_Vuejs_0"></a>Weather App by Vue.js</h1>
<h2 class="code-line" data-line-start=1 data-line-end=2 ><a id="_Current__Forecast_weather_data_collection_by__1"></a><em>Current &amp; Forecast weather data collection by</em></h2>
<p class="has-line-data" data-line-start="3" data-line-end="4"><a href="https://openweathermap.org/api"><img src="https://openweathermap.org/themes/openweathermap/assets/img/logo_white_cropped.png" alt="N|Solid"></a></p>
<p class="has-line-data" data-line-start="5" data-line-end="6"><a href="https://openweathermap.org/api"><img src="https://travis-ci.org/joemccann/dillinger.svg?branch=master" alt="Build Status"></a></p>
<p class="has-line-data" data-line-start="7" data-line-end="9">Vue_weather app is a cloud-enabled, mobile-ready compatible,<br>
Vue.js-powered java project.</p>
<h2 class="code-line" data-line-start=9 data-line-end=10 ><a id="Features_9"></a>Features</h2>
<ul>
<li class="has-line-data" data-line-start="11" data-line-end="12">Current Weather Status</li>
<li class="has-line-data" data-line-start="12" data-line-end="13">Search Cities to finf weather status</li>
<li class="has-line-data" data-line-start="13" data-line-end="15">Temprature</li>
</ul>
<h2 class="code-line" data-line-start=15 data-line-end=16 ><a id="Installation_15"></a>Installation</h2>
<p class="has-line-data" data-line-start="17" data-line-end="18">This Project requires <a href="https://vuejs.org/">Vue.js</a> v3+ to run.</p>
<p class="has-line-data" data-line-start="19" data-line-end="20">Install the dependencies and devDependencies and start the server.</p>
<pre><code class="has-line-data" data-line-start="22" data-line-end="26" class="language-sh"><span class="hljs-built_in">cd</span> vue-wr
npm install
npm run serve
</code></pre>
<p class="has-line-data" data-line-start="27" data-line-end="28">For production environments…</p>
<p class="has-line-data" data-line-start="29" data-line-end="30">vue-wr</p>
<h2 class="code-line" data-line-start=31 data-line-end=32 ><a id="Project_setup_31"></a>Project setup</h2>
<pre><code class="has-line-data" data-line-start="33" data-line-end="35">npm install
</code></pre>
<h3 class="code-line" data-line-start=36 data-line-end=37 ><a id="Compiles_and_hotreloads_for_development_36"></a>Compiles and hot-reloads for development</h3>
<pre><code class="has-line-data" data-line-start="38" data-line-end="40">npm run serve
</code></pre>
<h3 class="code-line" data-line-start=41 data-line-end=42 ><a id="Compiles_and_minifies_for_production_41"></a>Compiles and minifies for production</h3>
<pre><code class="has-line-data" data-line-start="43" data-line-end="45">npm run build
</code></pre>
<h3 class="code-line" data-line-start=46 data-line-end=47 ><a id="Lints_and_fixes_files_46"></a>Lints and fixes files</h3>
<pre><code class="has-line-data" data-line-start="48" data-line-end="50">npm run lint
</code></pre>
<h3 class="code-line" data-line-start=51 data-line-end=52 ><a id="Customize_configuration_51"></a>Customize configuration</h3>
<p class="has-line-data" data-line-start="52" data-line-end="54">See <a href="https://cli.vuejs.org/config/">Configuration Reference</a>.<br>
…</p>
<h3 class="code-line" data-line-start=54 data-line-end=55 ><a id="Script_54"></a>Script</h3>
<p class="has-line-data" data-line-start="55" data-line-end="106">&lt;script&gt;<br>
export default {<br>
name: “Home”,<br>
data() {<br>
return {<br>
api_key: “Your_api_key”,<br>
url_base: &quot;<a href="https://api.openweathermap.org/data/2.5/">https://api.openweathermap.org/data/2.5/</a>&quot;,<br>
query: “”,<br>
weather: {},<br>
};<br>
},<br>
methods: {<br>
fetchWeather(e) {<br>
if (e.key == “Enter”) {<br>
fetch(<br>
<code>${this.url_base}weather?q=${this.query}&amp;units=metric&amp;APPID=${this.api_key}</code><br>
)<br>
.then((res) =&gt; {<br>
return res.json();<br>
})<br>
.then(this.setResults);<br>
}<br>
},<br>
setResults(results) {<br>
this.weather = results;<br>
},<br>
dateBuilder() {<br>
let d = new Date();<br>
let months = [<br>
“January”,<br>
“February”,<br>
“March”,<br>
“April”,<br>
“May”,<br>
“June”,<br>
“July”,<br>
“August”,<br>
“September”,<br>
“October”,<br>
“November”,<br>
“December”,<br>
];<br>
let days = [<br>
“Sunday”,<br>
“Monday”,<br>
“Tuesday”,<br>
“Wednesday”,<br>
“Thursday”,<br>
“Friday”,<br>
“Saturday”,<br>
];</p>
<pre><code>  let day = days[d.getDay()];
  let date = d.getDate();
  let month = months[d.getMonth()];
  let year = d.getFullYear();

  return `${day} ${date} ${month} ${year}`;
},
</code></pre>
<p class="has-line-data" data-line-start="114" data-line-end="118">},<br>
};<br>
&lt;/script&gt;<br>
…</p>
<h2 class="code-line" data-line-start=118 data-line-end=119 ><a id="License_118"></a>License</h2>
<p class="has-line-data" data-line-start="120" data-line-end="121">MIT</p>
<p class="has-line-data" data-line-start="122" data-line-end="123"><strong>Free Software, Hell Yeah!</strong></p>
