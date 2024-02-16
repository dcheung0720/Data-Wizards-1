# Fatal Crashes Analysis by Team Data-Wizards

<h1>1. Research Questions and Goals </h1>
<ol>
    <li>
        What is there a difference in survival rates between sex?
    </li>
    <li>
        Does being in a specific seat increase your chance of survival in a fatal crash?
    </li>
    <li>
        Are there correlations among crashes between hour, day, month, and year?
    </li>
    <li>
        Which car brands have the highest fatal crashes?
    </li>
    <li>
        How many of those crashes are DUI related?
    </li>
</ol>
<p><b>Our goal is to discern how these factors correlate with fatalities, identifying potential risk factors to inform strategies for reducing future fatalities.</b></p>

<h1>2. Data Sources and Data Collection</h1>

<h3>a. National Highway Traffic Association's API</h3>
[NHTSA Crash API](https://crashviewer.nhtsa.dot.gov/CrashAPI)
<p>We fetched 130,000 fatal crashes from year 2018 to 2021 and performed analysis on it, which are all located in the "Anaylsis" directory.</p>

<p> To get the specific details of each crash of the 130,000 cases, we must make an separate api call for each case, which caused our single threaded code
to be bottlenecked by the synchronous API calls. To resolve the bottleneck issues, we ran the code in parallel using the <b>Concurrent Module</b>. The details of
how we accomplished it can be found under the "D Collect Process Scripts" directory with the name "Crash_People_collection.ipynb" </p>

<h3>b. Geoapify</h3>
[Geoapify Documentations](https://apidocs.geoapify.com/docs/places/#about)
<p>We used the Geoapify to augment our data by adding longitude and latitude information based on county and state to our crash lists information.</p>

<h3>c. Census Bureau</h3>
[Census Bureau](https://www.census.gov/data/tables/time-series/demo/popest/2020s-counties-total.html)
<p>We used the Census Bureau data to get approximate population in each county to calcualte the relative proportion of fatal crashes in them.</p>

<h1> 3. Results and Findings: </h1>

<h3>a. Findings 1: Fatalities by Sex </h3>
<ol>
    <li>
        <p>The pie chart below shows that: of all the crash fatalities between 2018 - 2021, male fatalities claims majority at over 73%.</p>
        <img src = "./Result Images/Fatality_by_Sex_Pie.png"></img>
    </li>
    <li>
        <p>This bar graph below shows that: of all the crash fatalities cases between 2018 - 2021, males has a higher fatality rates than females. This difference could be attributed by where are they are sitting</p>
        <p>To examine whether the difference in proportions is significant, we also performed a 2-Proportion Z test to compare the fatality rates between male and female. 
        We found a p value of approximately 0 so we can use the data as evidence that there is a difference in fatality rates between male and females.</p>
        <img src = "./Result Images/Fatality_Rate_by_Sex_Bar.png"></img>
    </li>

</ol>

<h3>b. Findings 2: Seat Position Fatality </h3>
<ol>
    <li>
        <p>The bar graph below shows that the driver seat has the highest number of fatalities while the back middle seat has the least number of fatalities. </p>
        <p>This is to be expected because the driver is always there to drive the car and not many people sit in the middle unless the car is filled.</p>
        <img src = "./Result Images/Fatality_by_Seat_Pos_Count.png"></img>
    </li>
    <li>
        <p> The bar graph below shows the fatality rate per seat position. </p>
        <p>As we can see, the driver seat also has the highest fatality rate and the back middle seat has the lowest fatality rate. This could be attributed to the fact most collisions are head on so the impact is closer to the driver.</p>
        <p>From the graphs, we can clearly see that the fatality rates are different across the different seat position but I have also used a Chi Square Test to test for homogeneity and found a p value of 0 so the fatality rates are indeed not the same.</p>
        <img src = "./Result Images/Fatality_by_Seat_Pos_Proportion.png"></img>
    </li>
    <li>
        <p>We have also created pairwise comparisons using a 2 proportion Z test between all the different seat positions. </p>
        <p>As we can see in the 2D chart, all the p values are 0 or approximately 0, meaning all seat positions have a significant difference in fatality rate between other seat positions.</p>
        <p>In other words, no 2 seat positions have the same fatality rates, and this could be attributed by a car is usually impacted in a fatal crash.</p>
        <img src = "./Result Images/Fatality_by_Seat_Pos_PairWiseComparison.png"></img>
    </li>
</ol>

<h3>c. Findings 3: Fatality by County </h3>
<ol>
    <li>
        <p>The map below shows the count of fatal crashes between 2018 and 2021. As we can see, the highest count of fatalities are in the bigger cities, which are
        to be expected because there are higher counts of drivers and thus result in a higher count of accidents. </p>
        <img src = "./Result Images/Fatality_by_County_Count.png"></img>
    </li>
    <li>
        <p>The map below shows the proportion of fatal crashes by a county's population. From the chart, most county proportions are similar to others but there are a 
        few outliers, which may be caused by a small county with a low population. The homogenious proportions may be attributed to similar driving safety laws that are
        in placed in all states. </p>
        <img src = "./Result Images/Fatality_by_County_per_Capita.png"></img>
    </li>
</ol>

<h4>c. Findings 4: Alcohol Involvement and Fatality </h4>
<ol>
    <li>
        <p>The bar chart below shows the what proportions of fatality crashes have alcohol involved. About 15% of fatal crashes have some sort of alcohol involved and 
        about 12% of them are above a BAC rating of 0.08, which is the legal drinking limit. </p>
        <img src = "./Result Images/Fatality_by_BAC.png"></img>
    </li>
    <li>
        <p> The graph below shows a logistic regression that attempts to predict the amount of alcohol a person had and whether a person will survive. This model has 
        a mean accuracy of about 79%. Overall, we think BAC is most likely not a good predicator for fatality. </p>
        <img src = "./Result Images/Logistic_Regression_Fatal_vs_BAC.png"></img>
    </li>
</ol>
<h3>a. Findings 5: Time correlation </h3>
<ol>
    <li>
        <p>The graphs below visualize the amount of accidents based on yearly/monthly,daily, and hourly timeframes</p>
        <img src = "./Result Images/yearly2.png"></img>
        <img src = "./Result Images/monthly.png"></img>
        <img src = "./Result Images/daily.png"></img>
        <img src = "./Result Images/hourly.png"></img>
    </li>
    <li>
        <p>This bar graph below shows that: of all the crash fatalities cases between 2018 - 2021, males has a higher fatality rates than females. This difference could be attributed by where are they are sitting</p>
    </li>

</ol>
