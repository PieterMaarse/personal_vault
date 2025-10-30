Original prompt:

I want to build a react app that shows users how much money they would receive for different values of gross income. They aim is to inform people of the cashflows regarding taxes and benefits for different levels of income. It should display a graph with on the x-axis the gross income and on the y-axis what would be the resulting money distribution. This distributions should show the gross income, income tax, and several benefits. For the website use Vite and Tailwind CSS. For now, keep the website very basic. I will ask an AI tool to build this website for me. What do I need to clarify before you build the app?

AI prompt:

Build a **React web app** using **Vite** and **Tailwind CSS**.  
The app should show Dutch residents how taxes and benefits affect their **net yearly income** for 2025. It should calculate **net income**, **taxes**, **social contributions**, and **benefits** for different gross income levels and visualize the results.

### Core Functionality

- The app models **the Netherlands in 2025** and all amounts are in **euros (€)**.
    
- Income is from **employment only**.
    
- Users can enter:
    
    - Income (monthly or yearly, with automatic conversion between them)
        
    - Age
        
    - Number of children (and optionally ages)
        
    - Filing status (single or couple)
        
- The app calculates the resulting yearly totals and displays them as:
    
    - **Stacked chart** with components:
        
        - Gross income
            
        - Income tax
            
        - Employee social security contributions
            
        - Each benefit (e.g., child benefit, housing allowance, in-work credit)
            
    - **Line overlays** for:
        
        - Net income
            
        - Effective marginal tax rate (EMTR)
            
- Calculations are based on Dutch 2025 rules (you can approximate or use known values):
    
    - **Income tax** brackets and rates (2025 schedule)
        
    - **National insurance contributions**
        
    - **Heffingskortingen (tax credits)** such as:
        
        - Algemene heffingskorting
            
        - Arbeidskorting
            
    - **Benefits (toeslagen)** such as:
        
        - Kinderbijslag (child benefit)
            
        - Kindgebonden budget (child-related benefit)
            
        - Huurtoeslag (housing benefit)
            
    - Benefits phase out with income according to Dutch rules or simplified linear tapers.
        

### Graph

- X-axis: gross yearly income (0–120,000 euro, step 100)
    
- Y-axis: stacked components (amounts in euros)
    
- Tooltips show all components and total net income.
    
- EMTR displayed as a line derived from finite differences in net income.
    
- Include legend and color coding for each component.
    
- Allow toggling between “Show Net Income” and “Show EMTR”.
    

### UI

- Simple responsive layout using Tailwind.
    
- Input form on top or left side, chart on the right or below.
    
- Inputs should update the chart dynamically.
    
- Include formatted euro values with thousands separators.
    
- Add explanatory text for what each component means.
    
- Display a short disclaimer: “Simplified model of Dutch 2025 taxes and benefits. For illustration only.”
    

### Technical details

- Stack: **Vite + React + TypeScript + Tailwind + Recharts**.
    
- Data definitions (tax brackets, credits, benefit formulas) stored in a separate JSON file.
    
- Use functions to calculate:
    
    `NetIncome = GrossIncome - Tax - Contributions + Σ(Benefits)`
    
    `EMTR = 1 - (ΔNetIncome / ΔGrossIncome)`
    
- Maintain modular code so formulas and parameters can be easily updated.
    
- Use a clean, modern Tailwind layout with clear labels and chart legend.
    

### Deliverables

- Fully working React app that runs locally via `npm run dev`.
    
- Includes example JSON file with 2025 Dutch tax and benefit parameters.
    
- Well-structured code: components for InputForm, Chart, and Calculations.
    
- Commented TypeScript for clarity.