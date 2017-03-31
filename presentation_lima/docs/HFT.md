## Experiments in High-Frequency Trading


Eric Aldrich,  Dan Friedman,  Kristian López-Vargas 
<!--Let's discuss scope of presentation (whole vs lab); Where do we mention Peter? etc-->

University of California, Santa Cruz

Experimental Finance Conference | Tucson, 2016


--------------------------------------------------------

## Motivation 

* Trading latencies have rapidly declined. 

* HFTs account for a large fraction of trades worldwide.

* Proponents: HFT increases liquidity, reduces transaction costs. 

* Opponents: The cost of HFT infrastructure is borne by investors; liquidity vanishes when most needed.

--------------------------------------------------------

## Research Plan  

* Existing data are insufficient to resolve the controversy.

* Experiments are a superior alternative to scientifically compare market formats in the presence of HFT.

* We use experiments (lab and field) to compare relevant market formats.

--------------------------------------------------------

## Research Design  

* **Examine 4 formats**:

    * Continuous Double Auction (CDA).
    * Three alternatives -- FBA, IEX, EBS. 

* **Two stages**:

    * Laboratory (ongoing).
    * Field (open tournament - early stage).
 
* **Outcomes and metrics of performance**: liquidity, stability, and transactions costs.
 
--------------------------------------------------------

##  Baseline Market Format

* Baseline market format: Continuous Double Auction (CDA) 

    * Organizes trade in nearly all major exchanges.
     
    * Orders processed immediately with price-time priority.
 
    * Speed technology is crucial.
    
--------------------------------------------------------

##  Alternative Market Formats
     
* Three alternative formats attempt to reduce the incentives for speed.
   
    1. Frequent batch auction (FBA): equal priority to orders received in the same batch (e.g. a tenth of a second).

    2. IEX: delays incoming orders by 350 $\smash{\mu}$s, allows hidden, “pegged” orders.
    
    3. EBS: within a narrow time window, randomizes the sequence in which orders are processed.
     
       
--------------------------------------------------------

##  Laboratory Implementation  

* Formats in simple laboratory environment:

    * Based on Budish, Cramton and Shim (BCS, 2015).
    
    * CDA and FBA

* Participants tune algorithms that place orders on their behalf. 

* Will add relevant features of modern exchanges one at a time. 

---------------------------------------------------------

## CDA Equilibrium in BCS
 
* No asym. info or inventory costs, everyone risk neutral.

* Bertrand competition, but equilibrium spread > 0. 
 
* Positive spread is related to jumps in $\smash{V(t)}$:
    
    * Maker sends a replace order.

    * Others try to buy (sell) at stale quote and liquidate at new
      fundamental ("snipe").
    
    * Sniping probability $\smash{\frac{N-1}{N}}$.
    
    * Sniping generates arbitrage rents paid by investors.

----------------------------------------------------------

## FBA in General

* Orders are (still) continuously time-stamped.

* Trading day divided into many equal-length _submission stages_ (of length $\smash{\tau}$).
 
* At closing, all standing buy (sell) orders are combined to generate a stair-step demand (supply) curve.

* Market clearing (equilibrium) price $\smash{p^\star}$ is computed, and infra-marginal bids and asks are executed at a uniform price $\smash{p^\star}$.

-----------------------------------------------

## FBA Equilibrium in BCS
 
* Bertrand competition: Zero bid-ask spread.
    * $\smash{\forall \tau > 0}$ (discontinuity between CDA/FBA).

* (Slow) firms supply $\smash{\bar{Q}}$ units of liquidity at zero spread.

* $\smash{\tau >> \Delta \delta \Rightarrow}$ no one invests in speed:

$$\smash{\frac{\Delta\delta \, \lambda_V}{\tau} \, \mathbb{E}(J) \, \bar{Q} < c_{speed} }$$

--------------------------------------------------------

## Pilot Experiment 

* Redwood II interface.

* Two market formats in the session: CDA and FBA. 

* Three 5-minute _trading days_ (periods), per format.

* Each trading day had two markets (groups of four traders). 
    
* Session lasted approx 100 minutes.

* Realizations matched across groups and formats.

--------------------------------------------------------

## Pilot Parameters    

* $\smash{\lambda_V=4}$: $\smash{V(t)}$ jumps every 4 seconds.
    <!--* Historical SPY ETF data $\smash{\Rightarrow}$ 5-min lab session corresponds to 1.5 min of market trading.-->
        
* $\smash{\lambda_I= 3}$: Investor arrivals every 3 seconds.
        
* $\smash{V_0 = 100}$: Order of magnitude equal to liquid equities.
        
* $\smash{F_V = N(0,0.5)}$.
<!--Standard deviation is relatively large to price increments in data, but the magnitude is arbitrary if subjects can scale spreads accordingly.-->

--------------------------------------------------------

## Pilot Parameters   
        
* $\smash{c_s= \$0.01/s}$.
<!--Roughly twice the cost (per symbol, per second of a trading day) for a premier microwave service.-->
        
*  $\smash{\delta_{slow} = 0.5s}$: About 10 times larger than actual
   Chicago $\smash{\rightarrow}$ NY latency, after accounting for our
   time scaling.
    
* In FBA, batch interval was 5 secs (1.25 secs, market time); reporting lag was essentially zero; default latency / interval = 0.1.

<!--(In our pilot experiment, the ratio is 0.5/5 = 0.10; in more realistic settings it might be closer to 0.01.)
<!--On August 10, 2016 we conducted a pilot experiment with a Redwood II prototype of CDA and FBA matching engines, using the interfaces shown in Figures 2 and 3. In each format, two groups of four players each completed three five-minute periods. Each period, stochastic realizations using λ_V= 4, λ_B=λ_S=λ_I= 3, F_V  = N(0,0.5), cs=$0.01/sec, τ = 0.5 sec and initial V = 100 were matched across groups and formats; each trading period here roughly translates to a 80 second segment on the NASDAQ OMX exchange for the high-volume SPY contract. In FBA, the batching interval was 5 seconds and the reporting lag was essentially zero.-->
<!--We found a weak uptrend for snipers in CDA, but the share never exceeded 43%; in equilibrium of the BCS model the sniper share is 75%. In FBA the sniper share trended down, as predicted in BCS equilibrium, and fell below 20% in period 3. Almost all other players were makers; Out shares were always miniscule. The share of traders choosing speed trended up in CDA as predicted, reaching almost ⅔ in period 3, and trended down (also consistent with prediction) in FBA, falling to 11% in period 3. -->

<!--(In our pilot experiment, the ratio is 0.5/5 = 0.10; in more realistic settings it might be closer to 0.01.)-->

<!------------------------------------------------------------>

<!--## Pilot Session-->

<!--* Simplest lab environment is adapted from BCS.-->
 <!---->
<!--* Single asset, single exchange, continuous price.-->

<!--* $\smash{V(t)}$: exogenous, compound Poisson process, jump rate $\smash{λ_V}$, jump distribution $\smash{F_V}$.-->
 <!---->
<!--* Automated investors: exogenous stream of market buy/sell orders, Poisson arrival rates $\smash{\lambda_I}$.-->

<!--* Traders control bots/algorithms which place orders on their behalf, conditional on market conditions and strategies (_{out, making, sniping}_, _{fast, slow}_).-->
 

<!-- The simplest lab environment is adapted from BCS. A single asset is traded on a single exchange, and price is a continuous variable. The fundamental value V(t) is determined exogenously by a compound Poisson process with arrival rate λ_V and jump distribution F_V. Players’ profit opportunities come from “investors” represented by an exogenous stream of unit market orders to buy (limit price very high) and to sell (limit price 0) with Poisson arrival rates λ_B=λ_S=λ_I.-->

--------------------------------------------------------

## CDA in the Lab

<!--![CDA experimental interface](img/CDA.png)-->

<img src="img/CDA.png" style="width:900px; align-content: center">

<!--Eric, the options for resizing in reveal.js depend on the available extensions and markdown "version" [ideas?]-->

<!--Layout Legend: 
CDA user interface in BCS environment. Traders use the action box (bottom right) to adjust choices at any moment during the trading period. To (re)enter as a market maker she clicks the “maker” button or just drags the “Spread” bar to adjust s. To (re)enter as a sniper, she clicks the “snipe” button. By clicking the “Out” button, a player cancels any limit orders, deactivates sniping bots and unsubscribes from speed services. The event history box (top left) displays the time path of the fundamental value V(t) as a piecewise constant blue line, the trader’s own bid and ask as black horizontal lines, investor transactions as green vertical lines, snipe events as red vertical lines, and other traders’ limit orders as gray horizontal lines. The information box (top right) displays the current bid-ask spread, other traders’ status and the cost of speed cs. The profit history box (bottom left) displays players’ accumulated profit at each moment of time.-->

<!--Figure Events Legend: 
The event history box indicates that player 1 is about 48 seconds into the trading day, and has been a maker for at least 30 seconds. Her current spread of 1.21 is the best (smallest) of the two current makers. Investors arrived around seconds 23 and 26 with market orders to buy and sell, respectively. The green vertical lines in the event history box at those times, and the corresponding upward jumps in the profit history box, show her resulting profit. Around second 30, V jumped from about 100 to 102 and player got sniped by player 4, reflected in the red vertical line connecting the stale quote to the new V and the corresponding drop in profit. Note that profit is flat between events if “Speed” is turned off, but has a slight negative slope (of cs) when “Speed” is activated.
-->

--------------------------------------------------------

## FBA in the Lab

<img src="img/FBA.png" style="width:900px; align-content: center">

<!--![FBA Interface](img/FBA.png)-->


<!--Figure Layout Legend: FBA user interface in basic BCS environment. The action box, information box and profit history box are essentially the same as in Figure 2. In the event history box (top left), the thin black horizontal line segments depict V(t), and the gray vertical lines separate the 5-second batching intervals. The color-coded ticks depict the order book at auction times: blue for own orders, lighter blue for other traders’ orders and light purple for investors. Trader 1’s own filled orders (and those of other traders) are indicated by a green (gray) dot behind the corresponding tick. The red tick shows the clearing price.-->
<!--Play / Events Legend:
 Total time 48 seconds. A buying investor arrived during the batching interval [20,25), and a selling investor arrived during the batching interval [30,35). In both batches, trader 1 had the best spread (at 0.9) and had an order filled profitably. 
 Snipers not depicted in the figure. -->


----------------------------------------------------

## Summary Results 

| | MAKER | SNIPE | Speed | Spread | NumTrades | RMSE |
| --- | :---: | :---: | :---: | :---: | :---: | :---: |
| **CDA** | | | | | | |
|P1 | 63.5% | 33.8% | 43.2% | 0.80 | 109.5 | 0.50% |
|P2 | 62.2% | 35.5% | 53.5% | 0.46 | 140.5 | 0.37% |
|P3 | 60.0% | 38.3% | 66.0% | 0.40 | 158.0 | 0.39% |
| **FBA** | | | | | | |
|P1 | 66.9% | 31.9% | 28.5% | 0.44 | 87.5 | 0.42% |
|P2 | 74.2% | 25.0% | 22.3% | 0.25 | 85.0 | 0.26% |
|P3 | 79.9% | 19.4% | 11.1% | 0.21 | 91.0 | 0.30% |
| | | | | | | |

--------------------------------------------------

##  Next Steps and Discussion

* Development and Productions.

* More realism in environment. 

* Evidence from the lab and tournaments will improve understanding of
  financial market design (help regulation and policy)

* Our infrastructure will be a contribution for future research. 

<!--Exploring these differing environments will contribute to fundamental knowledge regarding financial market design. By introducing features one at a time, we will make strong inferences about which environmental aspects shape observed outcomes. By holding constant the realized stochastic process across market formats in any given environment, we can draw causal conclusions regarding comparative performance. For example, we will be able to make clear statements such as “relative to the basic CDA baseline, the IEX format lowers trading cost by 5-8% in normal environment X, but increases value-at-risk by 20-30% in stressful environment Y.” Such statements should help focus conventional econometric analysis of market data, and even by themselves should be helpful for regulators and exchange officials. -->

<!--We have started the lab stage developing simple environments that allow for HFT. Our current progress and preliminary evidence are encouraging on the feasibility of the project and and the quality of the collected evidence. Further evidence from the laboratory and the implementation of tournaments will constitute valuable scientific knowledge on which formats best promote financial market liquidity and stability and, thus, help improve the design of financial markets. Our research infrastructure will be an important contribution for future research on financial market design. -->

--------------------------------------------------

##  Thanks to

* Center for Analytical Finance.

* Undergraduate programmers, Morgan Grant and Zach Petersen.

* University of Maryland postdocs, Darrell Hoy and David Malec.
