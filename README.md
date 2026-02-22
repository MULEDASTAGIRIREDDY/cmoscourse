# cmoscourse
   # lecture1 why do we need spice simulations?
    Before we study about SPICE simulations we need to know diference between the spice simulations and circuit design.
#circuit design
<img width="566" height="766" alt="image" src="https://github.com/user-attachments/assets/a07059bb-c5a0-4241-8552-1d73463d8d87" />

In circuit design we study about diferent arrangements of PMOS and NMOS which gives our required functionality like the functionality o arrangement shown in the above picture is INVERTER
   Where as in SPICE simlations we find the output characteristics of NMOS and PMOS in designed circuit.
   
<img width="530" height="250" alt="image" src="https://github.com/user-attachments/assets/17642813-b46e-4e38-b418-0d5bfd32bbed" />

<img width="518" height="233" alt="image" src="https://github.com/user-attachments/assets/079c7007-ccc3-4fb2-a530-273893151cf6" />


 The above picture shows about characteristics of PMOS and NMOS.
 From graphs we can observerealtion betwen V<sub>in</sub>.PMOS and NMOS curves are inverted  to each other.These graphs Vout vs Vin  decides about the delay of the transistor.By that we can tune W/L ratio for our required delay as W/L where W is width o transistor and L is length of gate oxide of transistor.These parameters afects current which inturn changes DELAY.
   In clocktree,crosstalk,physical design flow build on spice as all these concepts works on delay.

   WHY?

<img width="791" height="262" alt="image" src="https://github.com/user-attachments/assets/f4a414b0-7d7c-409a-9560-e1c20e5755b3" />
 Above figure shows as buffer circuit with a specifications and output load given in figure.To calculate delay function of a bufer circuit we can get it rom delay table which is o Input slew rate and Output load. 

 <img width="779" height="232" alt="image" src="https://github.com/user-attachments/assets/3248825d-64fc-49d3-80ce-0b901ca2d771" />
    these are the delay tables of CBUF1 and CBUF2.Here we can observe for same values o input slew rate and output load the delay is different due to diference in characteristics of NMOs and PMOS in buffer 1 and buffer2 because of different W/L ratio.we can find delays of Cbuf by using given tables.
  Where does this delay tables comes from?
  Are these models accurate to use in realtime?
  How to verify whether static timing analysis is correct?

  # 1.2 NMOS Introdction to basic element in circuit design - NMOS

  <img width="389" height="310" alt="image" src="https://github.com/user-attachments/assets/af81b472-6c8d-444d-a036-15bd7f2714f4" />

Construction of NMOS:
+ It is  4-terminal device
 >Source
 >Drain
 >Ground
 >Body
+ It consists of P-type substrate>
+ It has got 2 isolatin regions on both sides.It is use to differentiarte between beside  transistors.
+ It has 2 n+ diffusion regions at both sides in which one is SOURCE and other is DRAIN.
+ Gate oxide is spaced between these two n+ regions and on that Poly-Si or metal gate has been placed.
+ Tthe gate terminal drives NMOS.
+ Body terminal is connected directly to P substrate and it is grounded.It is important in     finding threshold voltage the NMOS.


   PMOS is also similar to this where Substare is N type and diusion region is P type.


   THRESHOLD VOLTAGE(Vt):It is a function o X,Y,Z which is a mathematical equation.
   * Vgs=0
   * we grond all other terminals.
   * Here we can observe that the substrate and diffusion looks like PN junction diode and these are connected back to back.
   * Both junctions are "OFF".so the resistance between S-D is high.
   * BY applyiing +ve voltahe to Vgs then poitive charge is deposited at gate terminal and due to accumuation of +ve charge.It repels the positive charge in PType Substrate leaving only _ve charges there.Now it's looking like  a Capacitor.
   *  Similar to fuctioning o PN junctin diode there is a ormation o depletion region whre majority charge carriers  has been repelled.
   *  By increasing gate voltgae more positiv echarge carriers gets repeled from p substrate near t gate oxide.
   *  by doing that the depletion region increase and eventually it converts in N-type region which is called as  inversion.
   *  The voltage whree this strong invrsion happens is called THRESHOLD voltage.
   *  FUrther increase of Vgs,as there are no +ve particles near gate area to repe.so it will aattracts negative  charges from heavily doped ntype region.By this the channel width increases but there is no change in depletion width.
   *  There is a formation of continuous connection between to difusion regions through channel ormed in substrate.
 
     # how body termial effects the THRESHOLD VOLTAGE?
  + To find threshold equation we use Body terminal by supplying voltage to body terminal.
      <img width="805" height="335" alt="image" src="https://github.com/user-attachments/assets/9b667770-a285-4022-bbdf-bd6b9921a51e" />
  + By supplying voltahr through Body terminal Vsb the depletion region increases as there is a formation of reverse bias at source but at drain its same.
  + Eventhough w eapply sam evoltage to this circuit a ssam eas supplying to a circuit wit body grounded,inversion is delayed and threshold voltage(Vgs) increases.
  + while we increase Vgs increases,due to Vsb neagative particles attracts by Vsb that has been accumulate dnear gateoxide and goes to source area.
  + Due to that the channel width at source termial is less compare to width at drain terminal.
  + for strong innversion w ened to apply more voltage which is termed as Vgs=Vt+V1 where Vt is Threshold voltage when VSB is "0".V1 is the excess voltage that we supplied when Vsb is supplied.
  + Vt is function of device parameters.
 
Threshold Voltage=
it depends on doping concentration,Vsb,Body effect coeicient(impacts of Vsb),fermi potential   and threshold volage when Vsb is Zero.
<img width="420" height="183" alt="image" src="https://github.com/user-attachments/assets/d9fd491c-beb1-471a-893f-bbe47a626e96" />
  we get all these parametric  valuses from Foundry.By giving these data to SPICE we get threshold voltage values.


# Resistive region of operation with small drain-source voltage

<img width="462" height="310" alt="image" src="https://github.com/user-attachments/assets/f2b4556e-b065-423f-95d0-bfc2f674e340" />

+ The volateg Vgs suppllied above Vt will increase channel length by inducing negative charges there.The more gate voltage we ar supplying more the channel width increases.
  induced charges(Qi)=Vgs-Vt
+ when we supply a small voltage such as 0.05V from Drain(Vds) by assuming Vt=0.45 and Vgs=1V.
   Here Vgs > Vt so the channel forms between source and drain.
+ There is a  formation o Voltage Gradient as Source potential is Zero and voltage is applied at Drain.

  <img width="527" height="422" alt="image" src="https://github.com/user-attachments/assets/0606ce1c-b20a-441e-9c70-5db4883961b5" />

    when we apply voltage at drain,there is a formation of voltage gradient due to which the volage is not same at all points along eective channel length.
  V(x) is voltage at point 'x' along channel
  Vgs-V(x) is gte to channel voltage at a given point.It is known as effective channel voltage.

Here the induced charges(Qi)= Cox(Vgs-V(x)-V(t))
<img width="262" height="151" alt="image" src="https://github.com/user-attachments/assets/707bba8f-91fa-45f2-b5d6-b04477b24877" />
  The ormula or Cox has been stated above by naming all parameters and contsnat values.

+ From device view there are 2 types of currents:
 + Drift current - Current due to potential difference
 + Difusion Current - current due to difference in carrier concentration.

+ Here we are stating drift current as there is Potential current.
 
  <img width="338" height="459" alt="image" src="https://github.com/user-attachments/assets/6aa7c299-b1c3-4c7a-996b-c7ca8c51dfe3" />

  Drain Current = Velocity of charge carriers * available charge carriers along channel width

  velocity Vn(x) = mobility* electric field

![WhatsApp Image 2026-02-22 at 18 08 40](https://github.com/user-attachments/assets/17ffd8c5-59f1-4311-84c8-f1b5e23b6b29)

As it is linear reggion of operation we should simpliy it to linear.

<img width="280" height="61" alt="image" src="https://github.com/user-attachments/assets/f4c280e0-679e-4d60-b39a-ab09c6d8a1a6" />
 The equation is simpliied into this form where kn' is Cox * mobility.
 still we simplify this equation into linear form.This equation is suitable only for Vds value is small.so we can neglect square term from the equation.So we get Id=Kn*(Vgs-Vt)

 <img width="299" height="186" alt="image" src="https://github.com/user-attachments/assets/60d01007-3596-4aa8-bfdf-896e6d230e65" />


 we need to find the impact of Vds and  Vgs on Id drain current.The NMOS  works in linear region only when Vds <= Vgs-Vt.
 + For calculating Id drift current for diferent conditions on Vgs and Vgs to find it's sweeping ranges we are using an engine to do all the work which is SPICE simulation to get drain current waveforms.



# SATURATION REGION(Vds>Vgs-Vt)

<img width="837" height="447" alt="image" src="https://github.com/user-attachments/assets/da97dbb7-286f-45a9-80bd-a3e94fb1f6da" />

 From above picture we can observe 3 types of behaviours:
 1)when Vgs-Vds > Vt
   <img width="338" height="459" alt="image" src="https://github.com/user-attachments/assets/6aa7c299-b1c3-4c7a-996b-c7ca8c51dfe3" />
   The channel width is same through out.

2)When Vgs-Vds=Vt

<img width="348" height="273" alt="image" src="https://github.com/user-attachments/assets/86223c4f-91e3-4f5f-9b7a-4dd3bf00b080" />
+ In this condition w ecan observe that the Vgs+1 hich is greater than threshold voltage but Vds=0.45 which i seu=qual to threshold voltage.
+ By these values we can observe that inversion takes place and charges also induced at source.
+ Whereas at Drain the voltge is of threshold voltage,there just inversion happens and field has not been induced.
+ we can observe that in above picture.We can see traingulation of channel width.
+ At drain end the channel got disappearing.This phenomenon is called as Pinch-Off region.

   Pinch off condition: Vgs-Vds <= Vt.

  3)Vgs - Vds < Vt,then the channel near drain completely disappers.

  <img width="349" height="280" alt="image" src="https://github.com/user-attachments/assets/787c34a2-8589-4162-9693-e1a920442dff" />

   Here in Saturatiopn region,we don't have dependency on Drain.
  Voltage over channel remains constant = Vgs-Vt

  <img width="306" height="153" alt="image" src="https://github.com/user-attachments/assets/84d43152-8205-49da-88e6-1a3e5c084d5a" />
  In the above equation,when Vds > Vgs-Vt,then the channel voltage = Vgs-Vt
Here Vds is nothing but the channel voltage.
so,drain current changes into shown form.
 <img width="263" height="39" alt="image" src="https://github.com/user-attachments/assets/d3d7b3aa-571d-4922-8e06-ebe756e41f7a" />
   It acts as constant current.so,it is called as saturation region.






# Introduction to SPICE.

 It is a software which contains predefined models to derive wave forms to calculate delays.

 <img width="779" height="425" alt="image" src="https://github.com/user-attachments/assets/efa8c994-32f2-4888-a755-8a3469549f02" />

 + In the above image the circled parameters are known as SPICE parametrs.These parameters are given by foundry.
 + The background required to understad SPICE simulation has been understood in previos lectures and stated final results in above picture.

   <img width="451" height="367" alt="image" src="https://github.com/user-attachments/assets/d17c625e-bd0e-402c-8112-e009067609ce" />

   For spice  setup we give SPICE Model parametrs and SPICE nerlist, where as spice netlist is about how we arranged MOSFET circuit as we are not able to give direct moset parameters to software.By that we get required graphs to find delay.


   # SPICE netlist
    <img width="756" height="303" alt="image" src="https://github.com/user-attachments/assets/b7b1e716-cca4-4147-b839-d3f2344b86dd" />
    In SPICE netlist connection
   + The body and Source has been Grounded.
   + Gate is connected to Vin which is known as variable input through resistor in between them to protect gate from damage.
   + Supplying drain Voltage which is known as Variable supply Voltage.
  
   #  L2 Circuit description in SPICE syntax

   <img width="785" height="296" alt="image" src="https://github.com/user-attachments/assets/3810679a-706e-48ec-be0b-4ca2635ebbbe" />
   To convert netlist into SPICE syntax we need to deine nodes.
   Node node a line where thre is no obstruction.Like that wehave to deine nodes.Toput it simply the line between two components is called as NODE.
   
   <img width="378" height="211" alt="image" src="https://github.com/user-attachments/assets/2fa6daef-e0fd-43ae-8d85-ef4c2be169af" />

      Nodes of circuit is stated above.

   <img width="777" height="247" alt="image" src="https://github.com/user-attachments/assets/b42fb777-0aa5-4798-bd98-aae3bda4fc5d" />

   Here they state about SPICE syntax.
   + Nodes are represented as Vdd,n1,0,0
   + In syntax M denotes MOSFET.
    + MOSFET is connected by 4 nodes is stated.
    + Type of MOSFET is decided by TECHNOLOGY file which contains SPICE parameters.
    + We also stated length and width parameters.
   + Resistor as R,connected to 2 nodes.
   + Vdd as drain Voltage,connected to 2 nodes.
   + Vin as Vin,connected to 2 nodes.
  
   #  L3 Define technology parameters
  <img width="304" height="359" alt="image" src="https://github.com/user-attachments/assets/7dccf746-3167-44a4-97c1-5f46589488b1" />

  These are parameters coming from Foundry.
  <img width="384" height="204" alt="image" src="https://github.com/user-attachments/assets/2b50e599-4eeb-4cf4-bf08-b11757444f2a" />
  we can us eit in SPICE by using .MODEL as stated above.Here we can state parameters in its respective positions as it has predeined positions for diffrent values.

  <img width="351" height="141" alt="image" src="https://github.com/user-attachments/assets/e563a996-18a9-41ef-b425-f2c8f8d9f388" />
  all these models can be stored in <b>.lib</b> format.This can be used in SPICE console as shown below.

  <img width="415" height="130" alt="image" src="https://github.com/user-attachments/assets/4be16644-921d-4685-a23f-232d69f4f21b" />


   # simulation commands
   For these simulation commands we should sweep Vin and Vdd for different values.


   # L4 First SPICE simulation.


 In this lecture we learn about opening and running SPICE in terminal.
+ leant about dirent terminal commands.
+ Learnt about different corners such as Typical corner(tt),slowfast(sf),fastfast(ff) corner.

  <img width="618" height="747" alt="image" src="https://github.com/user-attachments/assets/b16d4efa-cb40-4557-936b-6a4d607ee676" />

  we opened a file from sky130 and Id vs Vds simulation for diferent Vgs.

  <img width="624" height="402" alt="image" src="https://github.com/user-attachments/assets/3a507611-c4ff-407d-8db2-3ecc3e760185" />

  

# DAY2

 # L1 SPICE simulation for lower nodes

 <img width="851" height="477" alt="image" src="https://github.com/user-attachments/assets/a49e6a17-977a-441e-ab12-ff67b9401e11" />

 From this image we can obserev that graphs and coorelate with our equtions.
 + Blue line in picture is Vds= Vgs - Vt.
 + This equation divides total graph into two regions.
  + Linear Region.
  + Saturation Region.
+ About linear region we assume that Vds is small,so the equation acts as linear and we can observe that in the graph eventhough Vds is small it has impact on difusion current.So,we observe nearly linear graph.
+ About satration region withs its respective Vds,We observe its nearly consatnt as stated by equation which cntains modulation cator for better results.So we observe nearly constant value.
+ We can observe when Vgs is zero,Id is also Zero.
+ Id increases with Vgs.

Here we took dierent condition where W/L is same but W is changed to 0.375u and L to 0.25u by keeping all other values same.

<img width="1352" height="503" alt="image" src="https://github.com/user-attachments/assets/6d1d6c1e-8de2-4183-84eb-1a22030ec63b" />

Command has been given by saving file in .cir format in terminal.By using command rin we can get plots.

 # Observation1
<img width="888" height="387" alt="image" src="https://github.com/user-attachments/assets/fcea381a-2803-4571-b517-8f2c5322ed6e" />

+ In long channel device Drain current shows Quadratic dependence.
+ In short channel  device Drain current shows linear dependence when gate voltage is increasing where as in long channel device it shows Quadratic dependence.
+ This happens due to VELOCITY SATURATION.

Now we will plot Id vs Vgs with  Vds as constant


<img width="1769" height="876" alt="image" src="https://github.com/user-attachments/assets/78ad97fe-478a-4a88-9d50-498aed1b5c38" />

# Igs vs Vgs with constant Vdd
# For length of 1.2u and length  and length of 0.25u,Vds at 0,2.5 by varying  Vgs
+ for long channel,the curve is completely Quadratic.Difusion current changes in Quadratic natre with increase in Vgs
+ for short channel length
 + Id changes quadratic with low values of Vgs.
 + with increase in Vgs, Id changes linearly for constant Vdd.
 + This happens due to VELOCITY SATURATION.

<img width="639" height="287" alt="image" src="https://github.com/user-attachments/assets/dcace198-0f95-4cc7-bdb3-08ec42063f7f" />

+ For lower values of electric field velocity changes linearly
+ With increase in electric field(E),velocity eventually becomes constant.
+ This phenomenon is called VELOCITY SATURATION.
+ At higher fields(after Ec) velocity becomes constan due to scattering effect.

  So we need to add velocity constraint in the equation.

  <img width="596" height="295" alt="image" src="https://github.com/user-attachments/assets/a1671f4d-ce23-43eb-aeb8-3f27ff5fe72e" />

  By rederiving equation we get <img width="332" height="142" alt="image" src="https://github.com/user-attachments/assets/2c5dc6ee-a392-4833-896b-23ec64535435" />

  we simpliy above equation by using 2 difernt modes:
  + Long channel(>250nm)
  + short channel(<250nm)
    <img width="419" height="183" alt="image" src="https://github.com/user-attachments/assets/2caf5b37-a633-4dce-a472-47cea422badd" />
  + In both modes major working regions  regions are same.
  + In short channel we can observe extra region namely "velocity saturation".
 
    <img width="654" height="337" alt="image" src="https://github.com/user-attachments/assets/f3602f70-8688-4e3b-a3c7-e9df12412adb" />
For diffrent modes there are dierent equations:
+ CUTOFF mode:For this region Id=0 as Vgt<0.
+ For remaining all modes model equation is same.The only diference is in Vgt.
        <img width="330" height="95" alt="image" src="https://github.com/user-attachments/assets/3f1473ac-5e2a-4e3c-a7f9-4ea49c01fd35" />

   Vmin defined as minimum values among Vgt,Vds,Vdsat.
  here Vdsat is technology parameter known as saturation voltage.i.e. voltage at which device velocity saturates and is  independent of Vgs or Vds.

  <img width="217" height="63" alt="image" src="https://github.com/user-attachments/assets/9ae92a60-d8fe-4c62-a801-bdb545dfae89" />
+ case1:
 + When Vgt is minimum,this states that Vds is high and mode is "SATURATION" mode.
 + the equation changes as shown in picture.

   <img width="313" height="69" alt="image" src="https://github.com/user-attachments/assets/54a0d37d-d218-4149-8543-e244a5c1c1b3" />

+ case 2:
 + Vds is minimum.
 + when Vds is minimum we can state that MOSET  runs in resistive mode.
 + so,the equation is changed into above shown form.
 + For urthr simplification as Vds is samll,we can neglect lamda term.

+Case 3:
 <img width="414" height="92" alt="image" src="https://github.com/user-attachments/assets/0d464f4d-ae18-4719-9d78-c32bd21dffd2" />
 the above shown is basic equation o velocity saturation region.

   <img width="893" height="394" alt="image" src="https://github.com/user-attachments/assets/5e0e4cb0-1d15-4338-a02f-7035a693a300" />

 


For same W/L ratio but with lower channel length has Low peak current than device with higher channel length.

   # L5 Labs Sky130 Id-Vgs

   # L6 Labs Sky130 Vt



   <head>MOSET as a switch</head>

   MOS device characteristics:
   
   <img width="603" height="218" alt="image" src="https://github.com/user-attachments/assets/cdb4e6b2-5753-45aa-be37-23c97232443e" />

   By this figure we can state that the MOSFET can be used as  switch by varying Vgs.
   + When Vgs > Vt(Threshold Voltage) it acts as ON,with finite ON resistance.
   + When Vgs < Vt,it acts as OFF condition with ininite OFF resistance.
   + we are using mod for Vgs and Vt because for PMOS, the conditions are negative but or NMOS they are positive. 


   
   










   












   



  






 


 
 


   
   


   

    
  
     
       



   


   







  


   
 




 







  

  

  




 


      

  






  
  

    
 

