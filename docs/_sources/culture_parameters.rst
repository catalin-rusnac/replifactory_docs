Culture Control Parameters
===================
Parameters that control culture dilutions

``name``

    The name of the culture. Example: **E. coli** or **not inoculated**.

``description``

    A description of the culture. Example: **replicate 1** or **chemostat** or **turbidostat** or **morbidostat**.

``volume_vial``

    Volume of the vial in milliliters (ml). This is the liquid volume under the waste needle.

``pump1_stock_drug_concentration``

    Concentration of the drug in the pump 1 stock bottle. Typically this should be 0 - pump1 should contain drug-free medium
    The unit of this parameter can be any unit of concentration (e.g., mg/L, Moles/L, mM, %, etc.). It is not specified but must be the same unit across all parameters involving drug dose.

``pump2_stock_drug_concentration``

    Concentration of the drug in the pump 2 stock bottle. This is the highest concentration that can be achieved in the culture.
    The lowest nonzero concentration in the vial occurs when adding the smallest injectable volume of drug to the vial (limited by drop size ~0.05mL).
    The minimum inhibitory concentration of the culture should not be below the smallest injectable concentration (~1% of the stock concentration).
    The stock drug concentration should be at least the desired minimum inhibitory concentration (after adaptation)

``dose_initialization``

    Initial dose added to the culture immediately when the experiment starts. -1 to disable. If this value is set to a positive number, the culture will get diluted as soon as the experiment starts.
    This is useful if you want to inoculate the culture into a vial with nonzero concentration of the drug.
    If enabled, this dose should be at least 1% of the pump2_stock_drug_concentration to ensure that at least a small droplet of the drug is added.

``dilution_factor``

    Factor by which the population is reduced during dilution.
    For example, if the vial volume is 12 ml and the dilution factor is 1.6, the maximum volume of the culture during a dilution is 12 ml * 1.6 = 19.2 ml.
    A total volume of 7.2mL will be added at every dilution, but the ratio of pump1 and pump2 will be adjusted according to the stress increase parameters.
    To achieve chemostat or turbidostat conditions with minimal variation in OD, set the dilution factor to a small value (e.g., 1.1).
    Note that higher a higher dilution frequency limits the time window for OD-based growth rate estimation. With every dilution the valve has to open and close, and an additional fixed waste volume is pumped to fill the waste tubing with air.

``od_dilution_threshold``

    OD at which dilution occurs. -1 to disable OD triggered dilutions. This is useful for running replifactory in turbidostat mode.

``delay_dilution_max_hours``

    Maximum time delay between dilutions. -1 to disable time-triggered dilutions. To achieve a dilution exactly every 2h, set this parameter to 2 and od_diultion_threshold to -1.

``dilution_number_first_drug_addition``

    Dilution number at which dose_first_drug_addition is added. -1 to disable drug addition.
    The first initialization dilution is also counted; set this parameter to at least 2 if dose_initialization>0.

``dose_first_drug_addition``

    Drug dose at first drug addition. -1 to disable drug addition.
    The dose is added to the culture at the dilution number specified by 'dilution_number_first_drug_addition'.
    If enabled, this dose should be at least 1% of the pump2_stock_drug_concentration to ensure that at least a small droplet of the drug is added.

``dose_increase_factor``

    Factor by which the dose is increased at stress increases. The new dose is calculated as: new_dose = old_dose * factor + amount.

``dose_increase_amount``

    Amount by which the dose is increased at stress increases. The new dose is calculated as: new_dose = old_dose * factor + amount.
    This parameter is useful to increase the drug dose by a fixed amount, regardless of the current dose.
    If the current dose is much below 1% of the pump2_stock_drug_concentration, set this parameter to about 1% of the pump2_stock_drug_concentration.

``threshold_od_min_increase_stress``

    Minimum OD for stress increase to be allowed. Useful to prevent stress increases if the culture is not growing.

``threshold_growth_rate_increase_stress``

    Minimum growth rate for stress increase to be allowed. Useful to prevent stress increases if the culture is not growing.

``threshold_growth_rate_decrease_stress``

    If growth rate is below this value, stress is decreased by making one default dilution with pump1 only,
    lowering the drug concentration by 'dilution_factor'. Period of consecutive stress decreases is controlled by 'delay_dilution_max_hours'.

``delay_stress_increase_min_generations``

    Minimum number of generations between stress increases. Useful to throttle the stress increase frequency.



Growth Rate and Doubling Time
-----------------------------

In the context of cell cultures, the growth rate is a measure of how quickly the cells in the culture replicate. The doubling time, on the other hand, is the amount of time it takes for the culture to double in size.

The relationship between growth rate (r) and doubling time (t) is given by the formula:

.. math:: r = \log(2) / t

Where:
- \(\log(2)\) is the natural logarithm of 2,
- t is the doubling time.

In other words, the growth rate is the reciprocal of the doubling time (scaled by the natural logarithm of 2), and vice versa. If you have a high growth rate, you'll have a shorter doubling time, and if you have a long doubling time, your growth rate will be lower.

Let's consider some examples with different growth rates:

1. For a growth rate of 0, the doubling time is infinitely long. This means the culture is not growing.

2. For a growth rate of 0.1, the doubling time is:

   .. math:: t = \log(2) / 0.1

   Which is approximately 6.93 hours.

3. For a growth rate of 0.5, the doubling time is:

   .. math:: t = \log(2) / 0.5

   Which is approximately 1.39 hours.

4. For a growth rate of 1, the doubling time is:

   .. math:: t = \log(2) / 1

   Which is approximately 0.69 hours, or about 41.4 minutes.