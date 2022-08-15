# Ground Motion Simulation

!syntax description /Functions/GroundMotionSim

Creates a realistic ground motion simulation with given input parameters. The object generates a time-acceleration history using the process outlined in [!citet](SabettaPuglieseFiorentinoetal2021). The required function inputs M,R,and Vs30 correspond to the earthquake magnitide, source-to-site distance, and shear wave velocity at a depth of 30m, respectively. F, R_type and n are optional parameters that correspond to the style of faulting, the type of source-to-site distance being used and the random seed to be used. The Magnitude of an event is a measure of its strength, the source-to-site distance is how far from the event we are interested in estimating the ground acceleration at, Vs30 is a soil property that describes the propogation of waves through the soil. There are 3 distinct fault types that can be specified in the function: Strike-Slip, Thrust Fault, and Normal Fault denoted as 'SS', 'TF', and 'NF'. The source-to-site distance can be defined in one of two ways, either as Joyner-Boore distance or Epicentral distance which can be input as 'Rjb' and 'Repi'. **Listing 1** shows the distinction between these two commonly used distance measurements. The function values return in units of (g), so the scale_factor by default is set to 9.81


!listing test/tests/functions/ground_motion_sim/ground_motion_sim.i start=[Functions] end=[Postprocessors]


!media media/examples/ex15/DistFig.png
       style=width:100%;margin-right:0px;float:center;
       id=fig:source-to-site
       caption=Source-to-site distance measurements.


[sample] shows simulated ground motion generated from the set of inputs in the **Listing 1** Function block. As we can see, varying the seed gives slightly different results due to the randomly generated phase angles that are used to formulate the time-history. 

!plot scatter filename=test/tests/functions/ground_motion_sim/gold/ground_motion_sim_out.csv
              data=[{'x':'time', 'y':'func', 'name':'Ground Motion'}]
              layout={'xaxis':{'title':'Time (sec)'},
                      'yaxis':{'title':'Acceleration (g)'},
                      'title':'Simulated Ground Motion'}
              caption=Time series of a sample ground motion
              id=sample



!syntax parameters /Functions/GroundMotionSim

!syntax inputs /Functions/GroundMotionSim

!syntax children /Functions/GroundMotionSim

More detailed information on the development of this parameterized simulation method can be found at [!citet](SabettaPuglieseFiorentinoetal2021).

!bibtex bibliography

