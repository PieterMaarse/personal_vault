---
MOC:
  - "[[$SA Investeringen]]"
tags:
  - bron
type: ChatGPT
about:
  - ChatGPT deep research output over QUEST III, RHOMOLO, en NEMESIS
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
# Macroeconomic Foundations for Understanding QUEST III, RHOMOLO, and NEMESIS Models

## Introduction

The European Commission employs several sophisticated macroeconomic models – including **QUEST III**, **RHOMOLO**, and **NEMESIS** – to analyze innovation policies and their economic impacts. Each of these models represents a different approach to macroeconomic modeling: QUEST III is a **Dynamic Stochastic General Equilibrium (DSGE)** model, RHOMOLO is a **Spatial Computable General Equilibrium (CGE)** model, and NEMESIS is a **macro-econometric** model. For a policy researcher new to macroeconomic models, the variety of frameworks and technical terms can be daunting. This guide provides a self-contained introduction to the macroeconomic and technical foundations underlying these models. It is written in clear, accessible language for a reader with strong quantitative skills but little background in macroeconomic modeling.

We will cover the general principles and mathematical structure of each type of model, explain how they handle **general equilibrium** and **optimization**, and discuss key concepts such as **representative agents**, **heterogeneous agents**, **calibration**, and **estimation**. A major focus is on how innovation and long-run growth are modeled: we will explore how **Research & Development (R&D)**, **knowledge spillovers**, **endogenous technological progress**, **human capital**, and **absorptive capacity** are incorporated into these frameworks. Along the way, we use equations and simple diagrams to illustrate important points. We also include examples of how **policy interventions** – such as R&D subsidies or tax incentives – can be represented in each model type.

By the end of this guide, you will have a solid foundation in the theory behind DSGE, CGE, and macro-econometric models as they relate to innovation policy. This background will enable you to better understand and interpret the specifics of QUEST III, RHOMOLO, and NEMESIS, which you can study in detail separately. Let’s begin by examining each modeling approach in turn.

## 1. Dynamic Stochastic General Equilibrium (DSGE) Models

**DSGE models** form the backbone of modern macroeconomic theory and are the framework on which QUEST III is built. ==A DSGE model represents the economy as a system of equations derived from economic theory – typically the **optimizing behavior of agents** (households, firms, etc.) under **resource constraints** – combined with **market-clearing conditions** that enforce general equilibrium.== The term ==“dynamic” means these models explicitly track the evolution of the economy over time, “stochastic” indicates they include random shocks or disturbances, and “general equilibrium” signifies that all markets in the model economy clear simultaneously== (supply equals demand in each market).

**Key features of DSGE models include:**

- **Microeconomic Foundations:** Every behavioral equation in a DSGE model comes from the microeconomic optimization of agents. Households maximize utility, firms maximize profits, and often governments pursue defined objectives or follow specified policy rules. This makes the model **internally consistent** – the macro outcomes emerge from aggregated micro behavior.
    
- **Intertemporal Decision-Making:** Agents make choices not just for the present moment but with regard to the future. Households decide how much to consume now versus save for later; firms decide how much to invest in capital or R&D based on expected future returns. These decisions introduce **dynamic equations** linking today’s choices with tomorrow’s outcomes.
    
- **Rational Expectations:** In many DSGE models, agents form expectations about the future in a forward-looking, model-consistent way (often assuming full knowledge of the model’s structure). This means households and firms anticipate future policy changes or shocks and adjust their behavior immediately, rather than through trial-and-error. This assumption gives DSGE models strong predictive discipline, although some models relax it in favor of learning or adaptive expectations.
    
- **Representative Agents (usually):** A common simplification is to assume one or a few “representative” agents for each type (e.g. a single representative household that stands in for all households). This assumption makes the mathematics tractable because it avoids dealing with complex distributions of agents. We will discuss the implications of this in a later section. Some DSGE models incorporate heterogeneous agents, but ==QUEST III (in its standard form) uses mostly representative agents by country and sector==.
    
- **Equilibrium solved by Markets:** Prices (like wages, interest rates, etc.) adjust such that all markets clear. If there is a shortage or surplus in any market, prices move until supply matches demand. ==Thus, **general equilibrium** is achieved at each point in time (or in the long run, if there are frictions in the short run==). DSGE models enforce budget constraints and resource constraints exactly, ensuring that nothing “magical” (like free resources) appears – everything is accounted for.
    

**Basic Structure:** A simple DSGE model usually consists of equations for households, firms, and sometimes a government or central bank:

- _Households:_ In a basic setup, a representative household maximizes an intertemporal utility function. For example, a common formulation is:
    $$U = \sum_{t=0}^{\infty} \beta^t \, u(C_t, L_t)$$

    where $C_t$ is consumption in period $t$, $L_t$ might be leisure time (or negative of labor supply), $\beta$ is a discount factor $0<\beta<1$, and $u(\cdot)$ is a one-period utility function (often assumed to be increasing in consumption and leisure, with diminishing marginal utility). Subject to this, the household faces a **budget constraint** each period such as:
    $$C_t + I_t + B_t = W_t H_t + r_t K_t + \Pi_t + T_t$$
    
    which says ==consumption $C_t$, plus any investment $I_t$ (household purchase of new capital), plus net purchases of bonds $B_t$ (savings), must equal the sources of funds: labor income ($W_t H_t$, wage $W_t$ times hours worked $H_t$), return on capital ($r_t K_t$, interest rate times capital stock owned), firm profits $\Pi_t$ (if households own firms), plus any government transfers $T_t$ (which could be negative if it represents taxes paid).== The household chooses sequences ${C_t, H_t, B_t, I_t, K_{t+1}}$ to maximize $U$ given these constraints and initial assets.
    
    Solving this optimization yields **first-order conditions** such as the famous **Euler equation** for consumption:$$u'_C(C_t, L_t) = \beta \, E_t\!\left\{u'_C(C_{t+1}, L_{t+1}) \, \big(1 + r_{t+1}\big)\right\}$$
    ==which equates the marginal utility of consuming one more unit today with the discounted expected marginal utility of saving that unit and consuming it (with earned interest) tomorrow==. In plainer English, this condition ensures the household is optimally balancing consumption over time: if interest rates are high, the household has an incentive to save more (consume less today) to gain more consumption tomorrow, until these incentives balance at the optimum. Another condition might equate the **marginal rate of substitution** between leisure and consumption to the real wage, governing labor supply.
    
- _Firms:_ A representative firm (or one per sector) maximizes profit. Typically, a firm has a **production function** such as
    $$Y_t = A_t \, F(K_t, N_t)$$

    where $Y_t$ is output, $K_t$ is capital input, $N_t$ is labor input (employment), and $A_t$ represents total factor productivity (technology level) at time $t$. A common functional form is Cobb-Douglas, for example $Y_t = A_t K_t^\alpha N_t^{1-\alpha}$ with $0<\alpha<1$. The firm’s profit in period $t$ is
    $$\Pi_t = P_t Y_t - W_t N_t - R^K_t K_t$$

    where $P_t$ is the price of output (in a one-good model we can take $P_t=1$ for simplicity), $W_t$ is the wage, and $R^K_t$ is the rental rate of capital. The firm chooses $N_t$ and $K_t$ (in the short run, $K_t$ may be predetermined if capital takes time to install) to maximize profit. In a perfectly competitive market, this yields conditions:
    
    - $W_t = P_t \frac{\partial Y_t}{\partial N_t}$, so wage equals the marginal product of labor (the extra output from an extra worker).
        
    - $R^K_t = P_t \frac{\partial Y_t}{\partial K_t}$, so the rental price of capital equals the marginal product of capital.
        
    
    These conditions ensure firms hire labor and capital up to the point that their marginal contributions equal their costs. ==If firms have **monopoly power** (imperfect competition), they might set price above marginal cost, yielding slightly different conditions== (e.g. with a markup). ==DSGE models like QUEST III are often **New Keynesian DSGE** models, which include elements of imperfect competition and nominal rigidities== (more on that shortly).
    
- _Capital Accumulation:_ If firms or households invest in capital, the capital stock evolves over time. A typical accumulation equation is:
    $$K_{t+1} = (1-\delta) K_t + I_t$$
    
    where $\delta$ is the depreciation rate of capital (the fraction of capital that wears out each period), and $I_t$ is investment in period $t$. This equation shows how today’s investment adds to the capital stock for tomorrow, minus depreciation.
    
- _Government and Policy:_ DSGE models can incorporate a government that collects taxes, spends on goods or transfers, and possibly sets monetary policy (if the model includes a central bank and interest rates). For instance, a simple government budget constraint might be $G_t + T_t^{interest} = T_t^{tax}$ (taxes fund spending $G_t$ and maybe service on government debt). In many models, fiscal policy (tax rates, spending) can be exogenous or follow rules, and monetary policy is often described by a rule like a Taylor rule for interest rates. ==QUEST III, being used for policy analysis, includes a government sector and can simulate various fiscal measures== (like R&D tax credits, as we will see).
    
- _Shocks:_ ==The "stochastic" part means the model includes random disturbances – e.g. a productivity shock to $A_t$, a preference shock to household utility, a policy shock, etc.== These are typically modeled as random processes (often simple ones like AR(1) processes). Shocks allow the model to generate fluctuations (e.g. business cycles around the steady growth path) and to analyze how the economy responds to unexpected changes.
    

**New Keynesian Elements:** ==Unlike a pure classical model, QUEST III (and many policy-oriented DSGE models) includes **New Keynesian features** such as _nominal rigidities_ or _frictions_==. For example, prices or wages may not adjust instantly (modelled by costs of adjustment or Calvo-style sticky prices), which leads to short-run unemployment or output deviating from its flexible-price equilibrium. ==These features allow the model to reflect short-term demand-side effects and the influence of monetary policy==. In a New Keynesian DSGE, even though agents optimize, constraints like sticky prices mean not all markets clear instantly – but eventually they do, and the model still ensures consistency over time.

**Solution of DSGE Models:** ==Solving a DSGE model means finding a set of equations that characterize the **equilibrium path** of the economy. Typically, one finds a **steady state** (where variables grow at constant rates or are constant) and then linearizes equations around it to study dynamics== (this is how one derives impulse-response functions or conducts forecast simulations). Because agents are forward-looking, DSGE models are often solved using specialized algorithms that handle the expectations (e.g. using software like Dynare or custom code to solve systems of difference equations). The result is a set of equations describing how each variable moves over time depending on its past, expected future, and shocks.

In summary, DSGE models like QUEST III provide a **laboratory for policy analysis** where one can conduct “what-if” experiments grounded in robust theory. For instance, one can introduce an R&D subsidy and the model will show how optimizing firms and households respond over time, taking into account budget constraints and expectations. The strength of DSGE models lies in their theoretical consistency and clear cause-and-effect mechanisms. However, they often simplify reality (with representative agents and certain functional forms) and require careful calibration or estimation of parameters to ensure realistic results.

## 2. Computable General Equilibrium (CGE) Models and Spatial CGE

**Computable General Equilibrium (CGE) models** are another class of economic model that, like DSGE, enforce general equilibrium in the economy – all markets are considered simultaneously. However, CGE models differ in methodology and typical use. They are often used for detailed **sectoral or regional policy analysis** (trade, tax, regional development, etc.) and are calibrated to **real-world data** (like input-output tables). RHOMOLO, the Commission’s model for regional policy, is a **spatial CGE model**, meaning it extends the CGE approach to multiple regions with trade and factor mobility between them.

At their core, CGE models are based on the classic Arrow-Debreu general equilibrium framework: many goods are produced and consumed, and prices adjust so that supply equals demand in every market (goods, labor, capital, etc.). ==Unlike DSGE, most CGEs **do not explicitly model the intertemporal optimization with forward-looking expectations**==. Instead, ==they often consider a static equilibrium (one point in time, or a long-run equilibrium comparison before and after a policy change) or a sequence of static equilibria over time (in a **recursive dynamic** CGE). Let’s break down the features:==

- **Economic Actors and Markets:** ==CGE models include multiple **producers (firms)**, multiple **consumers (households)**, as well as the government and often a foreign sector (rest-of-world).== Each producer produces a distinct good or service (often corresponding to sectors like agriculture, manufacturing, etc.) using inputs according to a production function. Each household derives utility from consuming goods and possibly leisure. There are markets for goods and markets for factors (labor, capital, sometimes land or natural resources), and often a trade framework for exports/imports.
    
- **Microeconomic Assumptions:** Similar to DSGE, producers in a CGE model maximize profits (or minimize cost) and households maximize utility, but these decisions are usually modeled in a one-period (static) context. For example:
    
    - ==A firm in sector _i_ in region _r_ might have a production function $Y_{i,r} = F_{i,r}(K_{i,r}, L_{i,r}, M_{i,r})$ where $M$ could be intermediate inputs (materials) from other sectors.== They hire labor and capital up to the point where factor prices equal marginal productivity (if perfect competition).
        
    - A household in region _r_ might maximize $U_r = U(C_{1,r}, C_{2,r}, ..., Leisure_r)$ subject to a budget constraint $\sum_j p_{j,r} C_{j,r} = Y_r$ (income $Y_r$ from wages, etc., equals spending on goods). This yields demand functions for goods based on prices and income (often derived from utility functions like Cobb-Douglas or CES preferences).
        
- **General Equilibrium and Data Calibration:** ==The term “computable” highlights that CGE models are calibrated to actual data and solved numerically==. ==A CGE model typically starts from an observed **Social Accounting Matrix (SAM)** or input-output table for the economy.== This data provides consistent numbers for production, consumption, trade, income, etc., in a base year. ==Model parameters (like share parameters in utility or production functions, and elasticities of substitution between inputs) are chosen such that the model’s equations reproduce the base year data as an initial equilibrium. This process is called **calibration**.== For example, if households in the base data spend 30% of income on food, the utility function’s parameters are set so that the household’s optimal choice gives 30% on food when facing base prices.
    
    ==Once calibrated, a CGE model can simulate **counterfactual scenarios**==: one changes some policy or external condition (e.g. introduce a tariff, or increase productivity in a sector) and then re-solves the equilibrium to find a new set of prices and quantities that clear all markets. The difference between the new equilibrium and the old baseline gives the effects of that shock.
    
- **Static vs Dynamic:** Traditional CGE models are static; they compare two equilibrium states (before and after a shock) without explicitly modeling the time path between them. However, many CGE models are **extended to dynamic settings** in two ways:
    
    1. **Recursive Dynamics:** This approach links a series of static equilibria across periods. For example, the model will solve year 2025 equilibrium given the state of the economy, then update some stocks (like capital or population) for 2026, then solve 2026, and so on. Agents are myopic in this setup – they take current conditions as given each period without anticipating future changes (expectations are adaptive or static). This is computationally simpler and often used in policy models. ==RHOMOLO operates in a recursive dynamic manner: each period, investment decisions update capital stocks gradually, and migration adjusts labor, but agents don’t have perfect foresight of distant future policy changes.==
        
    2. **Forward-Looking Dynamics:** A few CGE models incorporate forward-looking behavior more like DSGE, solving for an intertemporal equilibrium (often using a perfect foresight assumption). These are more complex to compute and less common in practice for large models, but conceptually possible.
        
- **Spatial Dimension (RHOMOLO):** ==RHOMOLO is notable for its **regional granularity**. It covers each of the EU’s regions (NUTS2 level) as a separate “economy” within the model.== Each region has its own households, firms, and government, and they are linked through:
    
    - **Trade in goods and services:** Regions buy and sell goods to each other. ==Typically, CGE models use an **Armington assumption**, which means goods are differentiated by origin (a car produced in France is not a perfect substitute for a car produced in Germany)==. This allows the model to handle bilateral trade flows and calibrate to trade data. The model will have equations for import demand in each region as a function of relative prices.
        
    - **Labor mobility:** Workers may migrate between regions in response to wage differences (though often with frictions or only a share of labor mobile). ==RHOMOLO, for example, includes inter-regional labor migration with some costs or delays==.
        
    - **Capital mobility or investment flows:** The model can allow capital to flow where returns are higher, although ==RHOMOLO in practice often distinguishes local investment decisions from savings== (introducing a degree of financial market segmentation by region).
        
    - **Knowledge spillovers:** (More on this in the innovation section) ==A spatial model can include that R&D or productivity improvements in one region can benefit others== (especially nearby ones), capturing the idea of innovation clusters and diffusion across space.
        
- **Market Structure:** Many CGE models assume **perfect competition** in product and factor markets (price equals marginal cost, zero economic profit in equilibrium). However, ==RHOMOLO and others allow **imperfect competition** in some sectors==. For instance, ==manufacturing or services might be modelled with monopolistic competition (à la Dixit-Stiglitz) where firms produce differentiated varieties and charge a markup.== This affects how they respond to changes (e.g. introducing increasing returns to scale if variety increases with output).
    

_Illustration: The circular flow of income in a simple general equilibrium model. Households (left box) supply factors of production – labor, land, capital – to businesses (right box) through factor markets (bottom oval), receiving income in the form of wages, rent, and interest. They use this income to purchase goods and services produced by businesses in the product markets (top oval), generating consumer expenditure (demand). Prices in the factor and goods markets adjust such that the supplies and demands balance (general equilibrium). CGE models explicitly represent this circular flow for many sectors and regions, ensuring that all flows are accounted for and consistent._

==In a CGE model like RHOMOLO, **calibration ensures** that this circular flow holds true for each region and sector initially, and **simulation finds a new equilibrium** after a policy shock.== For example, suppose we simulate an increase in infrastructure investment in a given region. The model will compute how demand rises in construction (direct effect), how this increases wages and possibly attracts workers from other regions, how prices might change, and how all other sectors are affected as the economy finds a new equilibrium with higher public capital. ==It will also capture spillovers: neighboring regions might benefit from increased demand for their products or suffer if some of their workers migrate out.==

It’s important to note some differences between DSGE and CGE: ==DSGE models emphasize **dynamics and expectations**, often on a national level with aggregated sectors, whereas CGE models emphasize **sectoral and regional detail** under general equilibrium at a often comparative-static level==. ==CGEs are very useful for **distributional analysis** (which sectors, which regions gain or lose from a policy) and ensure that all accounting identities hold (government budget, trade balances, etc.). However, since many CGEs lack forward-looking behavior, they might not capture anticipation effects or the transition path== without additional assumptions. To incorporate something akin to investment or growth, ==CGE modelers often include **ad hoc dynamic equations** (like investment adjusts gradually based on differences between desired capital stock and current stock, as RHOMOLO does). This introduces dynamics without full optimization==: for example, RHOMOLO’s investment equation might say that if the return to capital in a region is above normal, investment in that region will increase until capital stocks gradually converge to the desired level.

In summary, **RHOMOLO** as a spatial CGE provides a powerful way to analyze **regional innovation policies** by simulating how an R&D investment or education program in one region affects not only that region’s economy but also others via trade, migration, and spillovers. It is a large system of simultaneous equations representing the whole EU economy split into regions and sectors, solved such that supply equals demand in every market each period (subject to frictions like imperfect competition or sticky adjustments). The model’s strength is in capturing **granular heterogeneity** (regional conditions, sector technologies) and **spatial interactions**. ==Its limitations are that it generally assumes a **long-run equilibrium perspective in each period** (so it might not handle short-term business-cycle deviations as well as a DSGE) and relies on **calibrated parameters** which must be chosen carefully from literature or smaller-scale estimates.==

## 3. Macro-Econometric Models

The third approach, exemplified by **NEMESIS**, is a **macro-econometric model**. ==This type of model is sometimes referred to as a **structural econometric model** or a **macro-sectoral model**. The philosophy here is different: rather than deriving every equation from micro theory, macro-econometric models combine theoretical relationships with **empirical estimation**.== They typically have many equations estimated on historical data to capture the observed behavior of the economy. These models were the mainstay of policy institutions before DSGE models became popular, and they remain in use because of their detailed treatment of different aspects of the economy and their strong empirical calibration.

**Key characteristics of macro-econometric models:**

- **Equation-based Structure:** The model consists of numerous equations describing various relationships in the economy. For example, there will be an equation for consumption, for investment, for employment, for prices, for export demand, and so on – often broken down by sectors or categories. Each equation might look like a regression equation estimated from data. For instance, a consumption equation could be:
    $$C_t = a_0 + a_1 \, Y^{\text{disp}}_t + a_2 \, C_{t-1} + \epsilon_t$$
    
    which says consumption $C_t$ depends on current disposable income $Y^\text{disp}_t$ (with marginal propensity $a_1$) and on last period’s consumption $C_{t-1}$ (capturing habits or smooth adjustment, with coefficient $a_2$), plus a random error term $\epsilon_t$. The coefficients $a_i$ are numbers obtained from econometric estimation (or set based on literature). This is a simple illustrative form; actual models might include interest rates, wealth, consumer confidence indices, etc., as additional explanatory variables.
    
- **Dynamic with Lags (Partial Adjustment):** ==Macro-econometric models usually include **lags** and **adjustment dynamics** in their equations. Economic agents may not jump immediately to optimum behavior after a shock; instead, behavior follows patterns observed in data.== For example, firms might only gradually adjust their investment or employment due to costs of adjustment or expectations. This can be captured by error-correction terms or adaptive expectations. ==**NEMESIS** explicitly includes _error-correction mechanisms_ and partial adjustment: if the desired investment (based on a long-run equation) is higher than actual, firms will increase investment but only gradually, according to an estimated speed-of-adjustment parameter.==
    
- **Adaptive or Bounded Expectations:** Unlike DSGE’s typical rational expectations, ==macro-econometric models often assume **adaptive expectations** or even entirely backward-looking behavior in some areas. NEMESIS, for example, is described as _time-recursive_ with adaptive expectations – meaning agents base decisions on past trends and slowly update.== Some modern macro-econometric models do incorporate some forward-looking elements (e.g. an expectation term if empirical evidence suggests it), but they generally do not assume everyone foresees and optimizes perfectly over infinite horizons.
    
- **Rich Sectoral Detail:** NEMESIS and similar models usually have a high level of disaggregation. As mentioned, ==NEMESIS has about 30 sectors for each EU country==, making it a multi-country, multi-sector model. This allows analysis of sector-specific policies (like R&D in manufacturing vs services) and their macro impacts. It shares this detailed nature with CGE models, but the equations for those sectors come from econometric estimations or calibrated relationships rather than strict optimization.
    
- **Policy and Institution Variables:** ==Macro-econometric models incorporate policy influences through specific variables: tax rates, government spending components, interest rates, etc.== Many such models include fiscal and monetary policy feedback rules or exogenous projections. For instance, there might be a monetary policy block that sets interest rates in response to inflation (if modeling a central bank’s behavior), or a government budget block that ensures debt evolves according to deficits.
    
- **Anchoring to Long-Run Equilibria:** Even though these models allow short-run disequilibria (like unemployment, output not equal to potential, etc.), they often include mechanisms to ensure that in the long run, key economic identities and equilibrium conditions hold. For example, an **Phillips curve** relationship may link inflation to the output gap in the short run, but ensure that in the long run inflation equals money-supply growth or some target. Or a **wage equation** might include unemployment (for short-run) but impose that eventually real wages equal labor productivity (for long-run). This mix of short-run dynamics and long-run equilibrium conditions is achieved through error-correction models: a typical form might be
  $$\Delta w_t = \gamma \, \big(\text{Productivity}_t - w_t\big) + \lambda \, \Delta p_t + \ldots$$
   
    meaning wage growth responds to the gap between current wages and productivity (closing that gap over time) as well as current inflation $\Delta p_t$ etc. Such formulation ensures wages do not drift arbitrarily from productivity in the long run.
    
- **Calibration to Literature:** ==Not all parameters are freely estimated; some that are hard to estimate (due to lack of variation or structural changes) might be **imposed from literature**. The NEMESIS model description notes that certain key parameters in the endogenous growth module (like the elasticity of innovation output with respect to R&D) are set based on robust findings in literature.== This is a pragmatic blend of calibration and estimation to ensure sensible behavior.
    

An example will help illustrate how NEMESIS works in practice: Consider the **investment behavior of firms**. In a DSGE, this came from solving an optimization with an Euler equation for capital. In a CGE, investment might be savings-driven or exogenously specified or adjusted via stock adjustment. In NEMESIS, a likely equation could be:
$$I_t^{\text{sector}} = b_0 + b_1 \,\text{Tobin's } q_t + b_2 \, \Delta Y_t^{\text{sector}} + b_3 \, I_{t-1}^{\text{sector}}$$
This mixes theory (Tobin’s q theory suggests investment depends on the ratio of market value to replacement cost of capital, indicating expected profitability) and empirical (a term for output growth $\Delta Y$ capturing accelerator effects, and a lagged investment term $I_{t-1}$ capturing partial adjustment). The coefficients $b_i$ would be estimated so that the equation reproduces historical investment patterns in that sector. The presence of $I_{t-1}$ with coefficient $b_3$ less than 1 makes it an **error-correction/adjustment** type equation – if desired investment jumps, only part of that jump is realized in one period.

Similarly, for **consumption**, a macro-econometric model might incorporate both forward-looking and backward-looking components (often called a _“hybrid” consumption function_):

- A proportion of consumers may be liquidity-constrained or rule-of-thumb spenders who consume based on current income (Keynesian behavior).
    
- Another proportion may be forward-looking, basing consumption on expected lifetime income (permanent income hypothesis), which could be approximated by including wealth or expected future income variables.
    

The final equation might thus be a weighted sum of an Euler equation solution and a Keynesian consumption function, with weights estimated or calibrated.

==**NEMESIS** is particularly geared towards **innovation policy**, so beyond the standard macro equations, it includes additional structure for **R&D and intangible investments**== (more on this in the next section). ==It distinguishes between **low-skilled and high-skilled labor** (capturing human capital aspects), and includes an **energy-environment module**== (important for analyzing climate policies). The model is solved recursively year by year, often using software that handles large simultaneous equation systems. One provides exogenous inputs (like world demand, commodity prices, policy settings) and the model projects the economy.

==The strengths of macro-econometric models are their **empirical realism and detail**. They can often closely fit historical data and thus give plausible near-term forecasts. They allow for **specific policy channels** to be analyzed in detai==l – for example, NEMESIS can simulate an increase in R&D tax credits and trace its effect on private R&D spending, then on productivity, then on output and jobs, while also considering short-run fiscal stimulus effects and long-run budget implications. ==They naturally incorporate phenomena like **business cycles, inertia, and market frictions** because those are observed in data and reflected in the estimated equations.==

==However, the trade-off is that they are **less theoretically rigorous** than DSGE models.== ==The lack of a unified optimizing framework means that one has to be careful about internal consistency==: modelers impose accounting identities and some equilibrium conditions to avoid nonsense results, but there isn’t a single “objective function” being maximized for the economy. Also, because many parameters come from historical estimates, ==the model’s validity depends on structural stability== – if a policy pushes the economy into a regime not seen in historical data, the predictions might be less reliable. For example, if analyzing a huge R&D subsidy that doubles R&D spending, the response in NEMESIS is based on historically estimated elasticity (perhaps from smaller variations), which might or might not hold exactly for large changes or in future contexts.

In conclusion, ==macro-econometric models like NEMESIS complement DSGE and CGE models. They are very useful for **short- to medium-term policy analysis and forecasting**, and for capturing a wide array of channels== (e.g. different types of innovation investments, distributional outcomes, environmental feedbacks). They bridge **micro and macro by using empirically estimated micro-behavior** (like consumption patterns of households) and **impose macro-coherence via identities**. Understanding NEMESIS requires comfort with reading regression-like equations and grasping which variables are endogenous or exogenous, and how policies are “fed into” the system – often via exogenous changes to certain variables or parameters that then ripple through the simultaneous equations.

Before diving deeper into innovation specifics, let’s summarize the differences between the three modeling approaches (DSGE, CGE, macro-econometric) in terms of how they handle core economic mechanisms:

- **General Equilibrium:** All three ensure overall consistency (no accounting black holes), but DSGE and CGE enforce market clearing systematically (DSGE in every period, CGE in each equilibrium computed), whereas macro-econometric models might allow short-run imbalances (like excess supply leading to inventory accumulation, or unemployment if wage adjustment is slow) but will respect budget constraints and long-run equilibrium tendencies.
    
- **Optimization and Behavior:** DSGE has explicit optimization by agents with constraints (strong theoretical micro-foundations). CGE usually has agents optimized within a single period (utility maximization and cost minimization), which is still micro-founded but lacks intertemporal optimizing (unless dynamic CGE variant). Macro-econometric uses a mix – some optimizing-inspired equations, some ad-hoc behavioral relations – essentially a data-driven representation of behavior.
    
- **Dynamics and Expectations:** DSGE features fully dynamic adjustment with forward-looking expectations (rational expectations if not stated otherwise). CGE is often static or recursive without forward-looking expectations (though it captures some dynamics via stock accumulation), meaning agents react to current and past info, not future policy changes that haven’t happened yet. Macro-econometric models include dynamic lags and sometimes partial expectation of future (e.g. via wealth effects or interest rate expectations) but are largely backward-looking or myopic compared to DSGE.
    
- **Calibration vs Estimation:** DSGE and CGE heavily use calibration (choose parameters to match certain ratios or elasticities from literature). DSGE models can also be **estimated** (e.g. Bayesian estimation on time series data, as some versions of QUEST have been). CGE models are rarely estimated as a whole, though particular elasticities (like trade or substitution elasticities) might come from econometric studies. Macro-econometric models are mostly estimated equation by equation on historical data, with calibration for some hard-to-estimate parameters. This means NEMESIS’s behavior is closely tied to empirical evidence, while QUEST’s behavior is tied to theoretical assumptions constrained by some data calibration, and RHOMOLO’s behavior is dictated by its calibrated equations and identities.
    

Now that we have outlined the three modeling approaches, we turn to the central theme for innovation policy: **how these models incorporate innovation, R&D, knowledge spillovers, and endogenous growth mechanisms.** This is crucial background for interpreting how a policy like an R&D tax credit can have long-run effects on productivity and output in each model.

## 4. Innovation, R&D, and Endogenous Growth in the Models

One of the major challenges in economic modeling is to represent **technological progress and innovation** – the engines of long-run growth. Traditional models like the Solow growth model treated technological progress as an **exogenous** factor (manna from heaven). Modern models, especially for policy analysis, try to make innovation **endogenous**: resulting from intentional activities like R&D, education, and investment in knowledge. The QUEST III, RHOMOLO, and NEMESIS models each incorporate endogenous innovation in different ways, reflecting their modeling philosophies.

### 4.1 Exogenous vs. Endogenous Growth: Solow Model Background

To appreciate the newer approaches, it’s helpful to recall the basic **Solow-Swan neoclassical growth model**, which is the baseline for exogenous growth. In Solow’s model, output is produced with capital and labor ($Y = F(K,L)$) under diminishing returns, and technology ($A$) grows at a constant exogenous rate. If $y = Y/L$ and $k = K/L$ denote output and capital per worker, the model’s steady state occurs where investment equals the “break-even” investment required to cover depreciation and labor force growth.

_Solow growth model diagram: Diminishing returns to capital per worker (the red curve $y=f(k)$) result in a steady-state $k_0$ where the investment in new capital (green curve $s,y$, with $s$ the saving rate) equals the amount needed to offset depreciation and population growth (black line labeled $(n+\delta)k$). At this steady state (point A), output per worker $y_0$ is constant. In the Solow model, long-run per-capita growth ($y$ rising from $y_1$ to $y_2$, for example) can only occur due to exogenous technological progress shifting the $y=f(k)$ curve upward – capital accumulation alone cannot sustain growth._

The Solow model tells us two important things: (1) Capital deepening has limits – without continual technological improvement, an economy converges to a zero-growth steady state in per capita terms; (2) Technological progress (often called **Total Factor Productivity, TFP** growth) is left unexplained (exogenous). This is unsatisfactory for policy questions, because it means things like R&D or education have no role in affecting the long-run growth rate (they could only affect the level of output or the speed of convergence in Solow’s world).

**Endogenous growth theory** emerged to fill this gap. Pioneering models by Paul Romer (1980s) and others brought innovation into the model as a result of intentional actions by firms or individuals:

- **Romer’s 1990 model (Endogenous Technological Change):** Romer introduced a formal R&D sector where researchers create **new designs (ideas)** that expand the variety of intermediate goods. In his model, the output used a production function like $Y = \sum_{i=1}^{N} x_i^{\alpha} L^{1-\alpha}$, where $N$ is the number of differentiated intermediate inputs (designs) and $x_i$ is the quantity of each input. The greater the number of designs $N$ (which represents the stock of knowledge or technology variety), the higher the productivity of labor, exhibiting **increasing returns to scale** overall (because ideas are non-rival – they can be used by many firms at once). The key equation is the **knowledge production function**:
    $$\dot{N} = \zeta \, L_R \, N^{\phi}$$
    
    where $L_R$ is labor employed in research, $\zeta$ is a productivity parameter, and $\phi$ captures how the existing stock of knowledge affects new knowledge production. Romer’s original idea had $\phi=1$, implying **knowledge has strong spillovers** – the more knowledge already exists, the easier it is to create more (standing on shoulders of giants). This led to a result that the growth rate of $N$ (and thus of output) increases with the scale of the economy ($L_R$). Later researchers like Jones (1995) argued $\phi<1$ – there are diminishing returns in research or duplication of efforts as the knowledge stock grows, which yields a model of ==**semi-endogenous growth** (growth rate depends on population growth in the long run, not just policy)==.
    
- **Schumpeterian models (Aghion & Howitt 1992, etc.):** These focus on **quality improvement** and creative destruction. Firms invest in R&D to invent better products that replace old ones. Growth comes from a sequence of quality ladders. While the micro mechanics differ (successive innovation races rather than expanding variety), the macro outcome is similar: R&D effort sustains long-run growth if appropriately incentivized.
    
- **Human Capital (Lucas 1988):** Another form of endogenous growth involves human capital $H$ – skills and knowledge embodied in workers. Lucas’s model had an equation $\dot{H} = \phi H u$, where $u$ is the fraction of time spent accumulating skills (like education or training). Human capital accumulation can drive growth by continually improving labor productivity. It can also complement R&D, since an educated workforce is necessary to conduct and implement innovation.
    

The common thread in these theories is that **investment in intangible assets** (knowledge, skills) can generate sustained growth, especially because of **spillovers** (one firm’s or person’s knowledge can benefit others). However, because knowledge spillovers mean private returns to R&D may be less than social returns, there is a rationale for policy intervention (subsidies, public research, etc., which is why government innovation policy matters).

Now let’s see how each modeling framework implements these ideas:

### 4.2 Innovation in DSGE (QUEST III and Endogenous R&D)

QUEST III is built to include an ==**endogenous growth mechanism via R&D**==. In fact, one version of QUEST III is explicitly called the “R&D model” and incorporates a semi-endogenous growth à la Jones, adapting Romer’s expanding variety setup. Here’s a conceptual outline of how a DSGE model like QUEST might model innovation:

- **Sectors:** ==In addition to households and final goods firms, the model has a **research sector**.== For example, _research firms_ use inputs (like researchers’ labor and maybe some capital) to produce new knowledge or designs.
    
- **Knowledge Stock:** Let’s denote by $A_t$ ==some index of technology or knowledge (it could be the number of distinct intermediate goods, or the stock of ideas)==. The evolution of $A_t$ is given by a knowledge production function, for instance:
    $$\dot{A}_t = \chi \, A_t^{\phi} \, L_{R,t}$$
    
    where $L_{R,t}$ is labor employed in research at time $t$, and $\chi$ and $\phi$ are parameters. If $\phi=1$, this is like Romer’s fully endogenous case (with scale effects: more existing knowledge makes research more potent). If $0<\phi<1$, it’s a semi-endogenous case (diminishing returns to knowledge stock in research). The model often uses $\phi<1$ to avoid unrealistic scale effects – QUEST III documentation mentions a Jones (1995) type mechanism, implying $\phi$ likely around 0 (meaning the growth rate of $A$ eventually depends on growth of research labor, e.g. population growth).
    
- **R&D Investment Decision:** Typically, R&D is costly – it uses up resources that could have been used to produce consumption or other goods. In QUEST, one might imagine intermediate goods firms or a dedicated R&D sector that invests in research in order to earn future profits (e.g. patents on new designs). A firm might face a condition like:
    
    _Marginal Cost of R&D today = Present Value of Marginal Future Profit from innovation._
    
    If there’s a patent system, the firm that discovers a new design might get monopoly profits on that design for some time. The DSGE being micro-founded will derive such conditions. For instance, if $V_t$ is the value of a new idea at time $t$, and $C_t^{R}$ is R&D expenditure, an optimality condition could be $C_t^{R}$ is chosen such that its marginal cost equals $\beta E_t[(\partial V_{t+1}/\partial A_{t+1})]$ etc. Without going into deep math, the result is: R&D investment increases until it no longer pays off at the margin. Policy like a subsidy can tilt this condition by reducing the effective marginal cost of R&D, thus encouraging more innovation.
    
- **Spillovers and Externalities:** In DSGE models, knowledge spillovers are often embedded by assumptions such as: an individual firm does not internalize how its R&D adds to the aggregate $A_t$ which benefits others. For example, in the knowledge production function above, each research firm might consider $A_t$ given (they are small relative to the whole stock). Thus there is an external effect – they ignore the $A_t^\phi$ part’s effect on overall productivity. Also, new knowledge might immediately become part of the public stock $A_t$ that all firms can use (non-excludable once created aside from the inventor’s specific profit on a design). This means the social return to R&D exceeds the private return, a crucial point for policy (government R&D support can improve welfare by bridging this gap).
    
- **Basic vs Applied Research, Diffusion:** ==The QUEST III model even distinguishes between _basic research_ (creation of new ideas, raising scientific knowledge) and _applied research_ (adoption of ideas into production)==. Basic research expands the frontier (increases $A_t$), while applied research or adoption determines how fast new technology is implemented in producing final goods. In the real world, a breakthrough (like a new general-purpose technology) might not raise productivity until firms learn how to use it – adoption lags. QUEST includes an adoption process, drawing on work by Comin and Gertler (2006) or similar, where firms expend resources to convert new ideas into usable technology (this could be modeled by another state variable, say $Z_t$ for general knowledge and $T_t$ for technology used in production, with $T_t$ catching up to $Z_t$ over time through effort).
    
    **Absorptive capacity** can come into play here: If a firm or country has very low own research or human capital, it might have trouble adopting frontier ideas. Some models incorporate this by making the adoption rate or effective research productivity depend on human capital levels. For instance, an adoption equation might look like $\dot{T}_t = \psi (Z_t - T_t) H_t^\vartheta$, meaning the gap between general knowledge $Z_t$ and applied knowledge $T_t$ is closed faster if the firm has more human capital $H_t$ (absorptive capacity $\vartheta$). In absence of explicit equations, absorptive capacity is qualitatively recognized: e.g., developing countries benefit from foreign R&D only if they have skilled workers to implement new technologies.
    
- **Intangible Capital and Output:** Once knowledge $A_t$ is created, how does it affect output? Commonly, it enters the production function as a multiplicative factor or by enabling new product varieties:
    
    - A simple reduced form is $Y_t = A_t F(K_t, L_t)$: $A_t$ raises TFP directly. As $A_t$ grows from R&D, all else equal, output grows.
        
    - In a variety model, $Y_t$ might be an aggregate of many intermediates, and $A_t$ (number of intermediates) raises productivity by spreading fixed costs or by specialization. The output might not depend on $A_t$ linearly but through something like $Y_t = \left(\int_0^{A_t} x(i)_t^{\alpha} di \right)^{1/\alpha}$, which yields increasing returns.
        
    - In QUEST, with basic vs applied, basic research raises an index of scientific knowledge $Z$ (non-rival, public good), while applied research increases the portion of that knowledge that firms actually integrate. So productivity might depend on $T$ (applied tech stock), which in turn is trying to catch up with $Z$.
        
- **Semi-Endogenous Growth:** Quest uses a **semi-endogenous growth** approach. This typically means that the **steady-state growth rate of technology** is tied to something like population growth or an exogenous component, rather than R&D investment alone. However, policy can permanently raise the _level_ of output by shifting the technology trajectory upward, and can influence growth during transition periods. For example, doubling R&D spending in the EU might not double the long-run growth rate forever, but it could accelerate growth for a few decades and lift the economy to a higher productivity path (level effect). In model terms, with $\phi<1$ in $\dot{A}_t = \chi A_t^\phi L_{R,t}$, constant $L_{R}$ growth (like from population) is needed for constant $A$ growth. If policy increases the fraction of labor in R&D, it will increase growth until a new balance is reached where the returns diminish.
    

To interpret policy simulations in DSGE: ==if you see QUEST III results, an **R&D subsidy** usually leads to short-run output **decreasing slightly** and long-run output **increasing**==. Why the short-run decrease? Because resources (labor) are reallocated to R&D from current production – less consumption good is produced initially (a sacrifice of current GDP for future gains). Households may also consume less and invest more in knowledge capital. Over time, as knowledge stock $A_t$ grows faster, productivity increases and output rises above the baseline, eventually outweighing the initial dip. ==The speed of this payoff depends on the model’s parameters for how quickly R&D translates to productivity and how strong the spillovers are==.

QUEST’s DSGE structure also allows an analysis of **short-run demand-side effects** if, say, there are underutilized resources. However, usually a DSGE at full employment won’t have demand slack to boost; instead, any government spending (like public R&D funding) crowds out something else unless monetary policy or some friction allows output to temporarily rise. But with New Keynesian features, QUEST can show some short-run stimulus if interest rates react or if wages are sticky (so increased demand for researchers might reduce unemployment among high-skilled in short run, for example).

### 4.3 Innovation in CGE and Spatial Models (RHOMOLO)

In a CGE model like RHOMOLO, innovation is modeled in a way that is consistent with the general equilibrium but usually more **reduced-form** compared to DSGE. That is, ==instead of deriving R&D from optimization, the model often imposes relationships that link R&D spending or human capital to productivity based on empirical evidence or assumptions.== Key aspects of how RHOMOLO and similar CGEs handle innovation:

- **Total Factor Productivity (TFP) as Driver:** Typically, each sector in each region has a TFP term that can change over time. In a baseline, these might grow exogenously (like assuming a 1% per year productivity growth, calibrating to historical trends). To introduce endogenous innovation, modelers allow **TFP to respond to R&D or human capital variables**.
    
- **R&D Sector and Spillovers:** ==RHOMOLO includes a broad “R&D and professional services” sector (NACE M-N) in each region. If the government increases R&D subsidies or spending in a region, it will directly expand demand for this sector’s output (which is essentially research services).== This increases that region’s GDP and employment in the short run in the R&D sector. More importantly, it is assumed to **boost the productivity** of other sectors either immediately or with a lag. One way to implement this is:
    
    - The model might accumulate a **knowledge stock** $K^{R\&D}_{r}$ for each region, based on past R&D spending (like an R&D capital stock). For example, $K^{R\&D}_{r,t+1} = (1-\delta_R) \, K^{R\!D}_{r,t} + \text{R\&D\_spending}_{r,t}$
        
    - Then the TFP in region $r$, sector $i$ could be a function such as $A_{i,r,t} = A_{i,r,0} \cdot \left(1 + \eta_1 \frac{K^{R!D}_{r,t}}{\text{GDP}_{r,t}}; + ;\eta_2 \frac{\sum_{s \neq r} w_{r,s} K^{R!D}_{s,t}}{\text{GDP}_{r,t}}\right)$.
        
		This hypothetical formula says: productivity grows as the stock of R&D in the region increases (term with $\eta_1$) and perhaps also with the R&D stock of other regions (weighted by $w_{r,s}$ which might decrease with distance or reflect trade links) – the spillover from external research ($\eta_2$ term). ==The coefficients $\eta_1, \eta_2$ need to be calibrated or estimated from literature== (for example, if empirical studies suggest an elasticity of output with respect to own R&D capital of 0.05 and with respect to others’ R&D of 0.02).
        
    
    If RHOMOLO cannot explicitly accumulate such stock in code, an alternative is scenario-based: ==modelers run a baseline where TFP grows at some rate, then in a scenario with more R&D, they **shock TFP growth rates** upward in proportion to the R&D increase, based on assumed returns. But newer versions like RHOMOLO V3 aim for more endogenous treatment via equations.==
    
- **Human Capital and Innovation:** RHOMOLO (and many CGEs) differentiate labor by skill (at least high-skilled vs low-skilled). Investment in human capital (e.g. education spending or on-the-job training) can be introduced by increasing the supply of high-skilled labor or by increasing the productivity of labor. For instance, a region with a better-educated workforce might simply have a higher effective labor input in production functions. ==Or the model can treat education similar to R&D: an education sector whose output raises a human capital index, which then boosts productivity.== Absorptive capacity can be implicitly captured because if a region lacks high-skilled workers, the effectiveness of R&D might be lower (the $\eta_1, \eta_2$ above could be made functions of skill ratio: no formal evidence that RHOMOLO does that explicitly, but it’s conceptually straightforward to imagine).
    
- **No Explicit Intertemporal Optimization for R&D:** ==Unlike DSGE, firms in a CGE aren’t choosing R&D to maximize profit. Typically, R&D spending might be largely driven by either government policy or some fixed saving/investment behavior==. So ==RHOMOLO might simulate a policy by simply injecting R&D funding rather than counting on firms to respond autonomously.== ==However, if there are market-driven R&D expenditures (say, private R&D responds to a subsidy), the modeler might introduce an _R&D demand function_ for firms, e.g. firms increase R&D spending if the subsidy lowers its price or if their output expands.== This could be modeled with an elasticity: a 10% subsidy could lead to, say, a 15% increase in private R&D spending if the price elasticity of demand for R&D inputs is 1.5. This elasticity could be set from micro studies.
    
- **General-Purpose Technologies (GPTs):** ==The RHOMOLO documentation mentions it can simulate different types of R&I== (e.g. general-purpose technologies). ==In a CGE, a GPT (like digital infrastructure) might be modeled as an increase in productivity across multiple sectors or as improved efficiency in producing certain inputs used economy-wide== (like ICT services become cheaper or more effective). The model might allow an R&D shock targeted at ICT sectors to propagate widely.
    
- **Path Dependency and Variety:** The documentation also notes RHOMOLO doesn’t explicitly model path dependency or differentiate product vs process innovation. This means it doesn’t keep track of variety count like a DSGE variety-expansion model, nor does it differentiate whether R&D improves products (quality) or processes (efficiency) – it all shows up as productivity increase (reducing effective input requirements for a given output or improving output for given inputs). Path dependency (lock-in to certain tech trajectories) is outside the model; it would need more state variables and history dependence than typically in CGE.
    
- **Calibration of Innovation Effects:** Ultimately, the effectiveness of R&D in the model is determined by parameters that likely come from empirical research (e.g. how much does 1% of GDP spent on R&D raise GDP in the long run?). Modelers might calibrate $\eta_1, \eta_2$ such that the model’s outcomes match known estimates (like an R&D elasticity of output of 0.05 at national level, and a portion of that attributed to spillovers).
    

To illustrate a **policy experiment in RHOMOLO**: Suppose the EU increases funding for regional R&D programs in poorer regions. In the model, this would be implemented as an increase in government spending directed to the R&D sector in those regions (and possibly a subsidy that reduces the cost for private R&D too). Immediately, the demand for labor in the R&D sector goes up in those regions, employing perhaps idle skilled labor or pulling some labor from other sectors. There is an immediate GDP boost (demand effect). Over time or in the equilibrium solution, the higher R&D activity translates into higher $K^{R!D}$ stock, which raises productivity ($A_{i,r}$) for industries in those regions (maybe starting next period or gradually). Higher productivity means those industries can produce output more cheaply, lowering prices, which improves their competitiveness. So, their output and exports rise. This creates **indirect effects**: other regions might see improved terms of trade (if the region with R&D now supplies them cheaper inputs) or they might face stiffer competition (if the region with R&D now produces goods more competitively that rival other regions’ goods). On net, because innovation is typically underprovided initially, one expects a positive overall EU GDP effect, with the targeted regions gaining relatively more (both from the direct stimulus and long-run growth). Some migration might occur: workers could be attracted into the high-R&D regions if wages rise there, which could slightly dampen the gains of the sending regions but also spread the innovation benefits.

One must be cautious reading RHOMOLO results: since it’s equilibrium, results might be reported as “after X years, GDP is Y% higher than baseline”. It doesn’t show a year-by-year transitional path (unless they run it period by period recursively). If they do recursive simulation (e.g. solving each year from 2021 to 2030), they could present a timeline: initial gains from spending, then growing productivity effect. The model will also show how sectoral outputs change, how employment shifts, and how prices/wages change by region.

### 4.4 Innovation in Macro-Econometric Models (NEMESIS)

NEMESIS, being explicitly designed to evaluate research and innovation policies, contains a rich set of relationships to model how R&D and other intangible investments affect the economy. Let’s outline how a macro-econometric model like NEMESIS handles these concepts:

- **Intangible Assets:** NEMESIS doesn’t only model R&D; it also includes **ICT investments** and **“Other intangibles”** (which may include software, training, organizational capital, etc.). This broad view acknowledges that innovation comes not just from formal R&D labs, but also from adopting new technologies (ICT) and improving workforce skills and business processes (training, etc.). Each of these can affect productivity.
    
- **Production Function with Intangibles:** Each sector in NEMESIS might have a production function incorporating these factors. For example, a nested CES production function where output depends on a combination of traditional inputs (labor, capital, energy) and an efficiency term that grows with intangible investments. Firms’ **effective productivity** could be something like:
$$A_{j,c,t} = \prod_{\text{type} \in \text{intangibles}} \left( 1 + \alpha^{\text{type}}_{j} \, I^{\text{type}}_{j,c,t-\ell} \right)$$

    where $I^{type}_{j,c,t-\ell}$ might represent past investment in intangibles of a certain type (with some lag $\ell$ before it affects productivity), and $\alpha^{type}_j$ are sector-specific impact parameters. For instance, if sector _j_ is manufacturing, R&D might have a higher impact on productivity than in a low-tech services sector, whereas training might have a substantial impact in services. These parameters would be calibrated/estimated from empirical studies or chosen to produce plausible elasticities.
    
- **Knowledge Externalities:** NEMESIS explicitly mentions **knowledge externalities between production sectors**. This means R&D in one sector can benefit other sectors’ productivity. For example, if the IT sector develops a new software tool, the finance sector’s productivity might improve when using it. Formally, the model might include terms like:
$$A_{j,c,t} = f\!\left(\text{own intangibles}_{j,c,t}, \; \sum_{m \neq j} \theta_{j,m} \, \text{R\&D}_{m,c,t}\right)$$

    where $\theta_{j,m}$ captures spillover from sector $m$’s R&D to sector $j$. Similarly, there could be **international spillovers**: the model might incorporate that part of TFP growth comes from foreign technology progress (e.g. an exogenous world frontier or weighted foreign R&D).
    
    A common approach is a **catch-up model**: sectors have an inherent productivity trend plus a term that depends on the gap between their productivity and the world frontier. R&D investment can help them catch up faster. In equation form:
$$\Delta A_{j,c} = \mu \, \big(\text{Frontier}_{j} - A_{j,c}\big) + \beta_1 \frac{\text{R\&D}_{j,c}}{Y_{j,c}} + \beta_2 \frac{\text{R\&D}_{\text{others in } c}}{Y_{j,c}} + \beta_3 \frac{\text{R\&D}_{\text{foreign}}}{Y_{j,c}}$$

    This says productivity growth has a part that is faster when you are behind (convergence) and parts that depend on R&D intensities (own, other domestic sectors, foreign). Each $\beta$ might be small but positive.
    
- **Absorptive Capacity:** In an econometric model, absorptive capacity can be represented by interaction terms. For instance, the benefit a sector gets from foreign R&D might be multiplied by its own R&D or human capital level. If data supports it, they could estimate something like: sectors with higher human capital enjoy more benefit from external knowledge (Cohen & Levinthal’s idea). Even if not explicit, including human capital as a separate explanatory variable in TFP growth captures that more educated workers make a sector inherently more productive and agile in using new tech.
    
- **R&D Investment Equation:** NEMESIS presumably includes an equation for how much R&D firms do. This might depend on profits, on policy incentives, and on expectations of demand. Possibly a formulation:
$$\frac{\text{R\&D}_{j,c}}{Y_{j,c}} = \gamma_0 + \gamma_1 \, \text{ProfitMargin}_{j,c} + \gamma_2 \, \text{Tobin's } q_{j,c} + \gamma_3 \, \text{SubsidyRate}_{j,c} + \ldots$$

    This would be an econometric relationship where if a sector has a higher profitability or a higher stock market valuation (Tobin’s q as a proxy for expected returns), it invests more in R&D. And if the government provides a subsidy or tax credit (reducing the effective cost of R&D), that directly increases R&D spending (the coefficient $\gamma_3$ captures how responsive R&D is to subsidies). Such an equation ensures that when you simulate a policy like a tax credit, the model endogenously increases R&D investment by firms rather than having to force it.
    
- **Lag Structure:** In macro-econometric models, **lags** are crucial. If R&D increases this year, perhaps only after some years will the full effect on productivity be realized (due to research taking time and diffusion delays). So NEMESIS might build in distributed lags: e.g., an R&D investment has a phased impact on TFP over, say, 5 years. This can be done via Koyck lag structures or by explicitly modeling an R&D capital stock as earlier. When simulating, the full GDP impact of an R&D policy might grow over time as these lags play out.
    
- **Policy Representation:** NEMESIS includes policy instruments like R&D tax credits and public R&D spending. Those enter the equations as follows:
    
    - Tax credit: effectively lowers the cost of R&D for private firms, which in the model might be captured by raising their R&D spending (in the R&D equation) and also directly cost to the government budget.
        
    - Public R&D: adds to R&D in sectors that receive it (maybe directly boosting R&D in certain sectors or in a public research sector). It could also have a different productivity impact than private R&D (some argue public research has wider spillovers but maybe less direct commercial output).
        
    - Education spending: would increase human capital supply (perhaps increasing the growth of high-skill labor or its productivity).
        
- **Short-run vs Long-run effects:** Because NEMESIS has Keynesian features in short-run (e.g. if demand rises and there’s slack, output can rise without immediate price increases), an innovation policy can have _two_ kinds of effects:
    
    1. **Demand effect:** If financed by government deficit or reallocation, it injects spending (e.g. hiring researchers, building labs) which directly increases aggregate demand and can multiply if there are idle resources. This effect happens quickly and can boost employment and GDP in the short term.
        
    2. **Supply effect:** As described, improved productivity raises output, lowers costs, and can improve competitiveness, leading to higher GDP in medium and long term. This effect grows over time and persists.
        
    
    Of course, there’s also the cost: if the policy is paid by higher taxes (now or later), that can crowd out some private consumption or investment. NEMESIS being comprehensive will account for that in government budget constraints. Often, simulations are done in a way that either holds something constant (like tax rates) and lets debt change, or vice versa, to isolate effects.
    

A simplified narrative of an **R&D subsidy scenario in NEMESIS**:

- Year 1: Government introduces a tax credit covering, say, 20% of R&D costs for businesses. Immediately, the effective cost of doing R&D drops, so firms increase their R&D projects. The model’s R&D equation bumps up R&D expenditures by, say, 10% in response (depending on elasticity). Government budget goes into deficit by the cost of the credit (unless offset by other taxes).
    
- Year 1 impact: The increased R&D spending means more demand for researchers, equipment, etc., which slightly increases GDP (demand effect). If there was unemployment, some researchers are hired instead of being idle, so output rises without much inflation pressure.
    
- Year 2-5: As firms perform more R&D, new innovations start coming out. Productivity in various sectors begins to improve. The model registers TFP growth a bit higher than baseline, gradually ramping up. Firms start producing more output with the same inputs, lowering their prices or expanding margins. Competitiveness improves, boosting exports. Employment might shift – maybe fewer workers are needed in some high-productivity sectors, but the overall higher output and income create jobs elsewhere (and R&D sector employment stays higher).
    
- Year 5-10: The full effect on productivity is realized. GDP is now significantly higher than it would have been without the policy, thanks to higher efficiency and possibly higher investment (as return on capital improved with productivity). However, the government has accumulated some debt due to the tax credit unless higher output generated enough extra tax revenue to offset (which sometimes it can partially – dynamic scoring).
    
- If the model includes an eventual budget closure (say taxes eventually rise to stabilize debt), that might slightly dampen the long-run gains by reducing consumption. But if the innovation boost is strong, the economy’s larger size can generate more tax revenue to help pay for the subsidy itself (this is the idea that an R&D subsidy can partially “pay for itself” by spurring growth, though usually not fully unless the spillovers are extremely large).
    

Comparing across frameworks, **NEMESIS** will likely show a larger short-run boost from innovation policy than QUEST or RHOMOLO, because NEMESIS allows Keynesian multipliers (especially if there is slack or if monetary policy accommodates). QUEST, being a DSGE, might show a short-run dip if resources are fully employed and reallocated, whereas NEMESIS might assume some underemployed resources are utilized (or even if fully employed, it might not enforce immediate crowding out, allowing a bit of short-run overshooting).

In the long run, all models should show a positive effect of a well-designed innovation policy, but the magnitude can differ. DSGE might be more conservative if it’s semi-endogenous (level effect but not growth effect beyond transition), CGE will depend on calibrated elasticities, and NEMESIS will reflect whatever its estimated elasticities and externalities suggest.

To wrap up this section: **human capital** and **absorptive capacity** in NEMESIS serve to amplify or enable the innovation process. A region or sector with strong human capital (education) will see more benefit from both its own R&D and from spillovers. This concept, while not always explicitly labeled “absorptive capacity” in model equations, is implicitly present. For example, if the model indicates that Southern Europe currently has lower innovation efficiency partly because of skill gaps, a policy mix that also increases training and education could enhance the effectiveness of R&D support there – something the model can simulate by jointly increasing education investment and R&D spending and observing a synergistic effect on productivity.

Having discussed how each model treats innovation, R&D, and knowledge spillovers, we can summarize a few cross-cutting **concepts** clearly:

- **General Equilibrium Feedback:** In all models, an innovation shock doesn’t happen in isolation – general equilibrium means there are feedback loops. Innovation increases productivity, which lowers costs, which can change relative prices, affecting trade and consumption patterns. A model user should consider these adjustments: e.g., some sectors may shrink if others become very productive (structural change), and some regions might lose workers to booming innovative regions (migration).
    
- **Externalities:** Knowledge spillovers are a prime example of externality (one actor’s actions benefit others without payment). All three models incorporate this, either implicitly (DSGE has A in production functions, CGE calibrates TFP effects, NEMESIS has cross-term elasticities). So they all justify why policy can improve welfare (because private market left alone underinvests in R&D).
    
- **Optimization vs Empirics in Innovation:** DSGE has clear optimization – which gives insight into _policy design_ (like how a subsidy affects R&D FOC). CGE and NEMESIS rely on assumed forms – which means results hinge on parameter choices (analyst must check sensitivity to those). For example, if one doubled the assumed spillover elasticity in a CGE, the long-run gains might double; whereas in DSGE, that elasticity is tied to deeper parameters like $\phi$ or returns to variety that are somewhat grounded in theory and empirical micro evidence on markups.
    
- **Calibration/Estimation of Innovation Parameters:** There is substantial uncertainty in real life about how much R&D translates to economic output. These models use different approaches: QUEST might use micro-estimates or set parameters to get plausible contribution of TFP to growth; RHOMOLO likely uses literature values or alignment with macro studies (e.g. Coe & Helpman’s international R&D spillover estimates); NEMESIS uses a combination of literature and its own regression analysis (perhaps calibrating to EU data on R&D and productivity).
    
- **Endogenous Growth vs Semi-Endogenous:** As mentioned, fully endogenous growth would mean a policy could permanently raise the growth rate of GDP (e.g. more R&D => forever higher growth, leading to divergent incomes over time). Semi-endogenous (as in QUEST) means policies have only temporary growth effects but permanent level effects. NEMESIS likely leans toward fully endogenous in spirit (they talk about endogenizing long-term growth via R&D policies). CGE, being often long-run comparative static, doesn’t inherently distinguish growth or level – if you run it in a steady-state mode, a policy might permanently raise growth until reaching a new steady state years later, but eventually, growth might return to the exogenous trend. If one integrates it in a truly dynamic way, one has to decide if there’s an exogenous component needed to sustain growth (like population or exogenous tech progress). If RHOMOLO doesn’t include an exogenous tech trend, then the only growth comes from accumulating factors and knowledge – in which case, increasing R&D could indeed permanently raise growth in the model as long as there’s no diminishing returns that eventually halt growth.
    

With these foundations established, we can now illustrate concretely **how a given policy (like an R&D subsidy or tax incentive)** is implemented and what it means in each type of model. This will help clarify interpretation when you encounter results from these models.

## 5. Policy Experiments: R&D Subsidies and Tax Incentives in Different Models

One common innovation policy is an **R&D subsidy or tax credit**, which lowers the effective cost to firms of investing in research and development. How do QUEST III (DSGE), RHOMOLO (CGE), and NEMESIS (macro-econometric) incorporate such a policy in practice? Here we provide a comparative walkthrough:

- **DSGE (QUEST III) – R&D Tax Incentive:** In a DSGE model, an R&D subsidy can be represented as a factor that reduces the marginal cost of R&D in the firm’s optimization problem. If a firm was deciding on R&D spending $R$ by equating marginal cost (say, one unit of final good per unit of R) to the expected marginal benefit (the future profit from new knowledge), a subsidy covering rate $s$ of the cost means the firm only pays $(1-s)$ per unit. In effect, the **first-order condition** for R&D changes to $(1-s) \cdot \text{Marginal Cost} = \text{Marginal Benefit}$. This leads to a higher chosen $R$ until the condition holds. QUEST would implement this by adding the subsidy into the equations – for example, the household’s budget constraint or government’s budget constraint reflects the subsidy payout, and the firm’s profit condition includes the subsidy. The government might finance this by higher taxes or borrowing (depending on scenario assumptions). When simulating:
    
    - Immediately, firms increase R&D investment. In the model’s equations, you’d see the R&D sector’s output jump. Resources (labor, maybe capital) shift towards R&D from other uses. If the model assumes full employment, some labor is reallocated from production to research – meaning slight dip in production of standard goods initially.
        
    - Over time, higher R&D produces more knowledge $A_t$, raising productivity. The model will show higher growth of output, consumption, and wages compared to baseline in the medium/long run.
        
    - If financed by higher general taxes eventually, households might consume a bit less to pay those taxes, but the long-run GDP ends up higher due to the knowledge-driven growth. The optimal policy balance (like how to finance it) can be studied by varying financing assumptions.
        
    - Because QUEST III includes nominal rigidities, if the R&D boom causes a demand shift, there might be a short-run interest rate response or inflation change (depending on central bank rule). However, R&D mainly affects supply-side, so it’s more of a structural policy than a demand stimulus. QUEST can also illustrate **short-run trade-offs**: maybe inflation stays low but output composition changes.
        
    
    The output of the simulation could be an impulse response or plots showing R&D spending up by X%, GDP initially -Y% then +Z% after a few years, etc. Interpreting these requires understanding all the above mechanisms.
    
- **CGE (RHOMOLO) – R&D Subsidy:** In RHOMOLO, one would implement an R&D subsidy by effectively lowering the cost of R&D sector output to the firms or by giving a budget injection. There are a few practical approaches:
    
    - Model a **negative tax on R&D labor or output**: e.g., reduce the wage paid by firms for researchers by 20% (government pays the rest). In equilibrium, this means at the same wage, firms demand more researchers (because cheaper), expanding R&D sector until equilibrium restored (wages might bid up a bit if labor was constrained, or if assuming infinite labor supply at fixed wage, they’d just hire more).
        
    - Directly increase **government demand for R&D services**: government buys additional R&D from the R&D sector equal to the subsidy amount (this is like financing research projects directly).
        
    
    Either way, the CGE will reflect:
    
    - **Resource allocation:** More labor and capital flows into R&D-intensive sectors. Possibly wages for high-skilled labor rise if they become scarce, which could crowd out some other skill-intensive production.
        
    - **Productivity effect:** The model would then increase TFP in sectors or regions as per its R&D-productivity linkage. For example, the region receiving subsidy sees its TFP in manufacturing grow a bit faster due to more local R&D.
        
    - **Fiscal aspect:** The subsidy has a cost. In a CGE, usually one might assume it’s financed by a lump-sum tax (neutral) or by adjusting government savings (affecting deficit). The choice will matter: a lump-sum tax effectively reduces households’ disposable income but without distortion. Often, CGE closures either keep government deficit fixed (and adjust a tax to pay for spending) or keep some tax rates fixed (and let deficit change). The analyst picks one.
        
    - **Equilibrium outcome:** Compare initial and new equilibrium: GDP of the subsidized region is higher. If one does it for all regions, overall GDP goes up by some percent. Some sectors expand (those benefiting from productivity or supplying R&D sector), some possibly shrink (if resources shifted away or if consumption pattern changes with income).
        
    
    For example, a result might say: an EU-wide R&D subsidy costing 0.1% of GDP per year leads to GDP being 0.5% higher after 10 years in the new steady state, with larger gains in high-tech sectors and leading regions, but some mild negative effects in sectors that didn’t innovate and lost relative competitiveness.
    
    Interpretation requires noting that CGE by default has full employment; so any increase in output is due to productivity or higher investment, not bringing idle resources online. If a region had unemployed labor and model allowed it (some CGEs have an unemployment equation or slack if wages are rigid at a floor), then part of the subsidy could employ previously jobless researchers, giving an extra boost. RHOMOLO might have some unemployment component (many regional CGEs allow for less-than-full employment or at least short-run Keynesian closure for labor).
    
- **Macro-Econometric (NEMESIS) – R&D Tax Credit:** In NEMESIS, implementing an R&D tax incentive involves changing the model’s exogenous policy variables:
    
    - Reduce the **user cost of R&D capital** or include a variable for “effective R&D price” that drops by the subsidy rate.
        
    - Alternatively, explicitly add a percent of private R&D financed by government in the equations.
        
    - The consumption/investment equations of firms will “see” this change. The model’s R&D investment equation will produce a higher R&D outcome (because it has a term for subsidy or after-tax cost).
        
    - The government budget equation will register a loss of revenue (unless the policy is financed by something, which one could simulate by increasing another tax or reducing spending elsewhere).
        
    
    On running the simulation:
    
    - **Short term (1-2 years):** Firms ramp up R&D projects. The immediate GDP effect could be positive for two reasons: extra R&D spending (demand) and any mild crowding-out is possibly offset by underemployed resources being utilized (NEMESIS being Keynesian in short run). So you might see a small uptick in GDP even in year 1, as opposed to the small dip we expected in DSGE.
        
    - **Medium term (3-10 years):** Productivity growth rate increases as the fruits of R&D appear. NEMESIS will show TFP gradually rising above baseline. Output, wages, and employment in sectors with innovation advantage increase. The model also likely shows a slight trade competitiveness improvement (more innovation, so maybe exports up).
        
    - **Budget feedback:** Over time, higher GDP leads to more tax revenues, offsetting some of the initial cost of the credit. If the model eventually requires stabilizing debt, it might raise some taxes in the long run, which would slightly dampen consumption – but ideally the net effect is still positive.
        
    
    A typical result might be: “R&D tax credit of 0.1% of GDP leads to GDP 0.6% higher than baseline after 15 years; the short-run multiplier is 0.2 (so a bit of immediate stimulus), and the long-run return on the policy is such that each euro of tax credit yields X euros of additional GDP or government revenue.” NEMESIS can output many indicators, like employment by skill (maybe more high-skill jobs created), inequality (maybe slight increase if high-skill benefit more), etc., given its detail.
    
    Interpretation is fairly direct because the model structure aligns with how policymakers often think (multipliers, elasticities). But one must remember these are model-dependent results: they rely on the estimated parameters that link R&D to growth. If those are too optimistic or pessimistic, the outcome scales accordingly.
    

In summary, each model incorporates an R&D subsidy through its unique lens: DSGE via altered first-order conditions and re-optimization; CGE via reallocation of resources and a new equilibrium with higher productivity; macro-econometric via direct stimulation of R&D spending and empirically driven productivity gains. All frameworks would agree on the qualitative story: R&D support increases innovation efforts, which then boost productivity and output over time, and that there are diminishing returns and lags involved. They also all account for the government’s cost – either requiring higher taxes or higher debt. A researcher should pay attention to how the scenario is set up in each case (e.g., is it deficit-financed or budget-neutral?) because that affects results.

## 6. Conclusion

This guide has covered the fundamental macroeconomic concepts and structures needed to understand the QUEST III, RHOMOLO, and NEMESIS models, especially in the context of innovation policy analysis. Let’s briefly recap the key points:

- **DSGE (QUEST III):** A micro-founded, dynamic model where economic outcomes are derived from the optimizing behavior of agents over time. It provides clarity on causal mechanisms (e.g., how an R&D tax credit changes firms’ R&D investment decision and thus technological progress) and ensures consistency via general equilibrium and rational expectations. QUEST III, as a New Keynesian DSGE, can capture both short-run demand-side effects (through sticky prices/wages and policy rules) and long-run supply-side growth (through semi-endogenous R&D-driven TFP). When interpreting QUEST, one should focus on things like the transitional dynamics, the role of expectations (e.g., anticipation of future policy can cause immediate jumps), and the steady-state versus short-run trade-offs (e.g., initial output loss vs long-term gain from innovation policy).
    
- **CGE (RHOMOLO):** A detailed general equilibrium model emphasizing the interconnectedness of sectors and regions. It strictly accounts for resource constraints and flow-of-funds in the economy, making it excellent for understanding how an innovation shock in one region spills over to others via trade, migration, and investment. It typically assumes equilibrium in each period (often full utilization of resources, unless specified otherwise), so results show how the _structure_ of the economy changes with policy (rather than transient booms or busts). Interpreting RHOMOLO outputs, you’d look at regional differences (who gains more, who gains less?), sectoral shifts, and consider that the model captures long-run outcomes after adjustments. It’s less about timing and more about who ends up where. Also, because it’s calibration-based, it’s important to note how sensitive results might be to key elasticity assumptions (usually reported in documentation).
    
- **Macro-Econometric (NEMESIS):** A policy-oriented model grounded in observed behavior and empirical relationships. It includes numerous channels by which innovation feeds into the economy: direct R&D effects on productivity, knowledge spillovers, human capital improvements, etc., all quantified by data. NEMESIS can illustrate both the short-term cyclical impact and the long-term growth impact of innovation policies, integrating them into one consistent simulation. When reading NEMESIS results, it helps to think in terms of multipliers and elasticities. For instance, by how much did employment or GDP increase per euro spent on R&D support? It’s also good to pay attention to what the model assumes about expectations – since it’s adaptive, a sudden policy change might have different effects than in a forward-looking model (e.g., agents might not immediately react until they see evidence of change).
    

Across all models, several **concepts repeatedly appear** which a researcher should be comfortable with:

- **General Equilibrium:** All markets and budget constraints are interconnected. An injection or shock in one part of the economy will reverberate through others until a new balance is found. This means always checking both the direct effects and the indirect effects (e.g., an innovation policy directly stimulates R&D sector – indirect effects: maybe increases wages for scientists, drawing them from elsewhere, or increases future productivity, lowering product prices and increasing real incomes, etc.).
    
- **Optimization and Behavioral Rules:** Understand whether behavior in the model is coming from solving an optimization (as in DSGE, or static optimization in CGE) or from an empirical rule (as in macro-econometric). In the former, if something seems odd, it might be due to an intertemporal trade-off (e.g., people saving more because they expect something). In the latter, it might be due to how the equation was estimated (e.g., consumers might react strongly to current income because historically that’s what data shows).
    
- **Representative vs Heterogeneous Agents:** QUEST largely uses representative agents (one per country or sector), meaning results are at an aggregate level (e.g., average household). RHOMOLO and NEMESIS have more heterogeneity (many regions, sectors, maybe multiple household types in NEMESIS like income groups). This affects interpretation: for instance, inequality aspects can’t be studied in QUEST (everyone is identical in a rep agent world), but NEMESIS might allow you to see if high-skilled vs low-skilled workers benefit differently from an innovation policy. If a model is rep-agent, you often interpret welfare changes in terms of that agent’s utility (which in QUEST might include consumption, leisure, etc.), whereas in heterogeneous models you might check a variety of indicators (regional GDP per capita, employment by skill, etc.) to assess distributional consequences.
    
- **Calibration and Estimation:** We stressed calibration vs estimation differences. For you as a researcher, this means when using or interpreting results, consider how confident one is in the parameter values. DSGE calibrations often come from either micro evidence or by matching a few macro moments. CGE calibrations come from accounting data and assumed elasticities from literature. Macro-econometric estimations come from historical correlations. Each has its pitfalls: DSGE might be off if the calibrated utility function doesn’t match reality (like assumed low labor supply elasticity, etc.), CGE might rely on an elasticity that, if wrong, linearly skews results, and macro-econometric might misattribute cause and effect or be affected by past policy regimes (Lucas critique: policy changes might alter the very behavior estimated historically). A savvy interpreter always checks sensitivity analyses if available.
    
- **Endogenous Growth and Spillovers:** The guide explained how growth can be endogenous (driven by model’s agents) or exogenous. Recognize in results if a model allows permanent growth changes or just level changes. For example, if QUEST (semi-endogenous) shows GDP level 10% higher after 20 years from a policy but same growth rate thereafter, that’s a level effect. If NEMESIS shows growth rate higher by 0.1% annually ongoing, it implies more endogenous growth (be mindful whether that’s realistic or if it assumes continuous increasing returns). Always tie back to the presence of spillovers: big effects usually come from amplifying mechanisms like spillovers. If a model did not include knowledge spillovers, the impacts of R&D policy would be much smaller because only the investing firm benefits – all these models include them, that’s why public R&D has a significant effect in these analyses.
    

Finally, as a beginning economic policy researcher, don’t be intimidated by the technical details. The purpose of these models is to provide _insights_ and _quantitative estimates_ for policy questions, not absolute truths. Use the framework presented here to ask the right questions when working with model results:

- _“What are the key drivers of this outcome in the model?”_ (e.g., was it capital accumulation, reallocation of labor, increased TFP from spillovers, etc.)
    
- _“How does the model’s structure shape this result?”_ (e.g., would this look different if agents were forward-looking vs myopic? If there were unemployment vs full employment?)
    
- _“Are there any important mechanisms absent?”_ (e.g., does the model include crowding-out via interest rates or not? Does it consider that not all firms can instantly use new tech due to absorptive capacity?)
    

By understanding the general equilibrium, optimization, and innovation modeling aspects covered in this guide, you will be well-equipped to interpret and critically evaluate the findings of QUEST III, RHOMOLO, NEMESIS, and similar models. You will be able to communicate their insights (and uncertainties) effectively to policymakers, noting, for instance, that **“according to the DSGE model, an R&D subsidy yields long-run gains but requires short-run sacrifices, whereas the econometric model suggests even short-run gains due to demand stimulus – implying that if there are idle resources, the policy could be win-win early on.”** Such nuanced understanding is the reward for mastering the macroeconomic foundations behind these complex models. Good luck with your further study of the models themselves, and may your analyses contribute to well-informed innovation policies!