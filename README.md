#  cmoscourse
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

   # Introduction — Why the Switch Model?

   Till now we learnt about gate voltage,threshold voltage,drain current from device point of view.Now we wil do for mosfet switch view.. The MOSFET switch model is a simplified but very powerful way to understand how digital logic works without solving complex equations.


1. The MOS Transistor Symbol

   <img width="700" height="375" alt="image" src="https://github.com/user-attachments/assets/f9709a16-743b-4e13-9de7-0a394e4bce64" />
   Figure 1 – MOS transistor symbol showing Gate (G), Source (S), Drain (D), and gate-source voltage |Vgs|

The MOS transistor has 3 terminals:
•Gate (G) — the control terminal. Voltage applied here controls whether the channel forms.
•Source (S) — carriers enter the channel from here.
•Drain (D) — carriers exit the channel here.

The controlling parameter is |Vgs| — the magnitude of gate-source voltage. This is compared against the threshold voltage |Vt| to decide the state of the transistor.
  Here we used modulus to generalise that the equations are acceptable for both NMOS and PMOS beacaus these are comlementary in nature.

2. Transistor as a Switch

<img width="688" height="338" alt="image" src="https://github.com/user-attachments/assets/7f3e04ea-3b46-4ba4-94f4-71d238e5f644" />
Figure 2 – MOS symbol (left) and switch equivalent (right). Transistor → Switch with infinite OFF resistance and finite ON resistance.


+ Transistor  as a Switch
   + With infinite OFF resistance when |Vgs| < |Vt|
   + With finite ON resistance when |Vgs| > |Vt|
     
<b>conditions</b>

+ <b> OFF State — |Vgs| < |Vt| </b>
  As no channel forms between S and D. The transistor is in the cutoff region. Resistance between S and D is effectively infinite. The switch is OPEN. No current flows regardless of Vds.

+ <b> ON State — |Vgs| > |Vt| </b>
 A conducting channel forms. The transistor is ON. Finite resistance exists between S and D. The switch is CLOSED with a series resistor. This resistance is called the ON resistance.

WHY is this useful?
In digital circuits we only care about two output states.They are:
1. HIGH (near Vdd) 
2. LOW (near 0).
3. The switch model captures this without needing the full I-V curves. It is much faster for understanding logic behaviour and delay intuitively.

+ The CMOS Inverter Circuit
    This is known as complemetary circuit as both PMOS and NMOS ollow complementary logic.

   <img width="700" height="438" alt="image" src="https://github.com/user-attachments/assets/60f1b250-9f70-4258-8a2f-444743a20b77" />
   Figure 3 – CMOS inverter schematic: PMOS source at Vdd, NMOS source at Vss, both gates driven by Vin, Vout at common drain node
  
The CMOS inverter has exactly 2 transistors:
•PMOS — source tied to Vdd, gate at Vin, drain at Vout(TOP)
•NMOS — source tied to Vss (ground), gate at Vin, drain at Vout(BOTTOM)
•Load capacitor CL at output — models the input capacitance of the next gate that can be connected to long wire or short wire.It could be anything.

Both gates are driven by the same Vin. The output Vout is taken at the common drain node between the two transistors.

Vgs depends on Vss and Vdd as shown below.This decides functioning.

WHY is PMOS source at Vdd?
Because VgsP= Vin - Vdd. For PMOS to turn ON, Vgs must be sufficiently negative, i.e., Vin must be significantly below Vdd. Tying the PMOS source to Vdd ensures this condition is checked correctly.

WHY is NMOS source at Vss?
Because VgsN = Vin - Vss = Vin. For NMOS to turn ON, VgsN must exceed Vtn. Tying the source to ground means VgsN = Vin directly, so the NMOS turns ON when Vin exceeds Vtn.



4. Case 1 — Vin is HIGH (Vin = Vdd)
 <img width="700" height="438" alt="image" src="https://github.com/user-attachments/assets/06f4593d-6c50-4fe3-8c0c-45d4740e73f6" />

 By Observation:
For PMOS:   VgsP = Vin - Vdd = Vdd - Vdd = 0 V
Since |VgsP| = 0 < |Vtp|  →  PMOS is OFF (open switch)

For NMOS:   VgsN = Vin - Vss = Vdd - 0 = Vdd = 2 V
Since VgsN  > Vtn  →  NMOS is ON (closed switch with resistance Rn)

<img width="700" height="475" alt="image" src="https://github.com/user-attachments/assets/1c5cb835-cdad-4481-9c0b-a3ecb04b9c79" />
Figure 5 – PMOS turns OFF (open switch, left) and NMOS turns ON (closed switch with Rn, right) when Vin = Vdd 

Equivalent Circuit for Vin = Vdd,with output load C1

<img width="840" height="506" alt="image" src="https://github.com/user-attachments/assets/c075d2a1-2e30-4dff-a763-97f42153753a" />


The equivalent circuit shows:
•Vdd → open switch (PMOS OFF) → Vout   — no path from Vdd to output
•Vout → Rn (NMOS ON) → Vss = 0 V   — output pulls down to ground

In steady state, PMOS is off so no current from Vdd. NMOS pulls Vout down to 0 V through Rn. CL discharges to 0 V.

Result:   Vin = Vdd (HIGH)  →  Vout = 0 V (LOW)

This is the correct inverter behaviour — a HIGH input produces a LOW output.

At this operating point, PMOS is off and NMOS is in the linear  region — it behaves like a resistor Rn pulling the output to Vss.


5. Case 2 — Vin is LOW (Vin = Vss = 0 V)

 we find equations and equivalent circuit for  Vin is high similarly we need to find it for  Vin=0 also.By combining those we will get complete circuit to eva;luate delay of cell/device.
 
<img width="815" height="475" alt="image" src="https://github.com/user-attachments/assets/cb021ac0-3cff-400a-904c-9b84e49d19f8" />

 let Vdd=5V, gate to source volatge 

   
By Observation:
let Vdd=5V
For PMOS:   VgsP = Vin - Vdd = 0 - Vdd = -Vdd = -5 V
It turn on the PMOS.Negative Vgs should be less than _Vts to turn ON and viceversa or NMOS.

For NMOS:   VgsN = Vin - Vss = 0 - 0 = 0 V
Since VgsN = 0 V < Vtn  →  NMOS is OFF (open switch)

<img width="803" height="506" alt="image" src="https://github.com/user-attachments/assets/d4528075-d66b-4c4a-95ff-088040e37396" />


Equivalent Circuit for Vin = Vss
The equivalent circuit shows:
To represent PMOS we se resistor as wires has some resistance and it is denoted by Rn.
+ It is non linear function of drain current.
+ NMOS is shown as open switch because Vin is zero,Vss is also 0,so there is no potential dierenc.

•Vdd → Rp (PMOS ON) → Vout   — Vdd charges output through Rp
•Vout → open switch (NMOS OFF) → Vss   — no path from output to ground

<img width="181" height="318" alt="image" src="https://github.com/user-attachments/assets/1f5abf4f-0db3-481e-954d-f15e8610fdd2" />


+ When input voltage is Vin = Vdd,the eqvivalent circuit is shown in above figure.First ciruit is for PMOS is of and NMOS is ON.
  
<img width="181" height="289" alt="image" src="https://github.com/user-attachments/assets/7d5e4910-9a08-4b26-99dd-f724436e93ed" />

when Vin=0,the equivalent circuit is shown above.

The above circuits decides voltage characteristics.



6. Summary — CMOS Inverter Switching Behaviour
Truth table by switch model
•Vin = Vdd (HIGH)  →  PMOS OFF, NMOS ON   →  Vout = 0 V (LOW)
•Vin = Vss (LOW)   →  PMOS ON,  NMOS OFF  →  Vout = Vdd (HIGH)

WHY CMOS has zero static power?
In both steady-state cases, one transistor is always OFF. This means there is no direct current path from Vdd to Vss at any time in steady state. No DC current flows, so no static power is dissipated. This is the biggest advantage of CMOS over older logic families like NMOS-only or bipolar logic.

ON Resistance and Delay
The ON resistance values Rn and Rp are not equal in general. They depend on:
•W/L ratio of each transistor
•Carrier mobility (electrons in NMOS are faster than holes in PMOS, so Rn < Rp for equal W/L)
•Supply voltage Vdd


# 

Introduction – What are we studying in this lecture?
In the previous lectures we understood the construction of NMOS, its threshold voltage, linear and saturation regions of operation, and also the concept of velocity saturation in short channel devices. Now in this lecture we move one step forward and look at the behaviour of PMOS and NMOS together inside an INVERTER circuit when the input voltage Vin switches between logic HIGH (= Vdd) and logic LOW (= 0V).
The core question we are asking in this lecture is: "What exactly happens inside the transistors — physically and electrically — when Vin goes HIGH or LOW?" Understanding this is critical because the answer to this question directly decides the output Vout, the switching behaviour, and ultimately the delay of any digital circuit built using CMOS technology.
The inverter circuit we are studying is shown in the picture below. It consists of:
•PMOS (M1) – connected between Vdd (top) and Vout
•NMOS (M2) – connected between Vout and Vss (ground)
•Load capacitor CL – connected between Vout and Vss, representing the next stage gate capacitance
•Input Vin – applied to the gate of both PMOS and NMOS

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/1aab1cb1-7347-4f51-9ad7-ad4b0d7c0124" />

Case 1: When Vin is HIGH (Vin = Vdd)
Let us first analyse what happens when the input voltage Vin is equal to Vdd, which is the logic HIGH condition. At this point we have two transistors in the circuit — PMOS at the top and NMOS at the bottom — and both of them see the same gate voltage Vin = Vdd.
What happens to PMOS when Vin = Vdd?
To understand PMOS behaviour we need to recall one important fact from our previous lectures: PMOS is a complementary device to NMOS. In PMOS, the substrate is N-type and the diffusion regions are P-type. Because of this, the PMOS transistor turns ON only when the gate voltage is sufficiently lower than the source voltage. The controlling parameter for PMOS is VgsP = Gate voltage – Source voltage of PMOS.
In our inverter, the SOURCE of PMOS is connected to Vdd. So:
•VgsP = Vin – Vdd
•When Vin = Vdd, VgsP = Vdd – Vdd = 0V
•Since VgsP = 0, which is NOT more negative than the PMOS threshold voltage (|Vtp|), the PMOS does NOT turn ON
•Therefore, PMOS turns OFF when Vin = Vdd

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/459a6be1-6498-4f19-937b-60154e52b01d" />

What happens to NMOS when Vin = Vdd?
Now for NMOS, the SOURCE is connected to Vss = 0V (ground). So:
•VgsN = Vin – 0 = Vin = Vdd
•Since VgsN = Vdd which is much greater than the NMOS threshold voltage Vtn, the NMOS channel forms strongly
•NMOS turns ON when Vin = Vdd
So when Vin = Vdd — PMOS is OFF and NMOS is ON. Now what does this do to the output?
Equivalent circuit when Vin = Vdd
From the above figure we can observe that when PMOS is OFF it acts as an OPEN CIRCUIT — meaning there is NO path from Vdd to Vout through PMOS. At the same time, when NMOS is ON, it acts like a resistance Rn between Vout and Vss. This creates a direct conducting path between Vout and Vss through the NMOS channel.
From our knowledge of basic circuits, when there is a direct path between Vout and Vss (0V) and no path from Vdd to Vout, the output capacitor CL will discharge through NMOS resistance Rn, and eventually:
•Vout = 0V = Vss = logic LOW

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/bd59cb1f-7b35-498b-ab93-c76e8090f4e7" />
When Vin = Vdd → PMOS OFF → NMOS ON → Direct path exists between Vout and Vss → Vout = 0

Case 2: When Vin is LOW (Vin = 0V)
Now let us analyse the second condition where the input voltage Vin = 0V, which is the logic LOW condition. Again, both PMOS and NMOS gate voltage is 0V. Let us see what each transistor does.
What happens to PMOS when Vin = 0V?
For PMOS, the SOURCE is still at Vdd. So:
•VgsP = Vin – Vdd = 0 – Vdd = –Vdd
•Since VgsP = –Vdd which is very negative and well beyond the PMOS threshold voltage (|Vtp|), the PMOS channel forms strongly
•Therefore, PMOS turns ON when Vin = 0V

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/cd84b895-3b62-43c1-8b7e-a0c51e08922c" />
Fig 4: When Vin = 0V — PMOS turns ON (gate voltage goes sufficiently below Vdd = source)

What happens to NMOS when Vin = 0V?
For NMOS, the SOURCE is at Vss = 0V. So:
•VgsN = Vin – 0 = 0V
•Since VgsN = 0V which is below the NMOS threshold voltage Vtn, no channel is formed in NMOS
•NMOS turns OFF when Vin = 0V

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/86da7373-9aba-4828-9f2c-2894a929ed96" />
Fig 5: When Vin = 0V — PMOS turns ON and NMOS turns OFF (no channel formed in NMOS)

Equivalent circuit when Vin = 0V
From the above figures we can observe that when PMOS is ON, it acts like a resistance Rp between Vdd and Vout. At the same time NMOS is OFF and acts as an OPEN CIRCUIT — meaning there is NO path from Vout to Vss through NMOS. This creates a direct conducting path between Vdd and Vout through the PMOS channel.
Since there is a direct path from Vdd to Vout and no path from Vout to Vss, the output capacitor CL will charge up through PMOS resistance Rp, and eventually:

•Vout = Vdd = logic HIGH
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/6efe8bba-4875-4a70-8a89-d760d12f2f48" />
Fig 6: Equivalent circuit for Vin = 0 — PMOS acts as Rp, NMOS is open. Direct path between Vdd and Vout results in Vout = Vdd

Case 2: When Vin = 0 → PMOS ON → NMOS OFF → Direct path exists between Vdd and Vout → Vout = Vdd


Combined View – Both Cases Together
Now from the above picture (Frame 12) we can see both cases side by side clearly. When we compare the two cases:
•When Vin = Vdd → Vout = 0 (output goes LOW when input is HIGH)
•When Vin = 0 → Vout = Vdd (output goes HIGH when input is LOW)
This is exactly the INVERSION behaviour that gives the INVERTER its name. The output is always the complement (opposite) of the input. This is achieved by cleverly combining PMOS (which turns ON when gate is LOW) and NMOS (which turns ON when gate is HIGH) in a complementary way — which is why the technology is called CMOS – Complementary Metal Oxide Semiconductor.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/8dce9462-c8fb-4b32-8e24-e698cd7a24d2" />

Fig 7: Both cases side by side — When Vin = Vdd, Vout = 0 (Rn path, NMOS ON); When Vin = 0, Vout = Vdd (Rp path, PMOS ON)
We can observe from the above image that the equivalent circuits are "mirror images" of each other. In both cases, one transistor acts as a resistor providing a conduction path while the other is completely OFF as an open circuit. This ensures no direct path from Vdd to Vss exists at the same time, which is critical for avoiding short-circuit current and maintaining proper logic operation.

Important Voltage Parameters – VgsP, VgsN, VdsP, VdsN
In this part of the lecture, the instructor introduces the voltage parameters that we need to carefully track for both PMOS and NMOS. These parameters are critical because they determine which region (cutoff, linear, saturation) each transistor is operating in at any given time.
From the figure below we can observe the labelling of terminals for both PMOS and NMOS in the inverter:
•G = Gate
•S = Source
•D = Drain
•VgsP = Gate to Source voltage of PMOS
•VgsN = Gate to Source voltage of NMOS

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/442a7d6f-59fe-43f8-bd24-38bc19e1c5ab" />
Fig 8: Terminal labelling — G, S, D for both PMOS and NMOS with VgsP and VgsN defined
Now adding the drain-source voltages as well:
•VdsP = Drain to Source voltage of PMOS (note: for PMOS, current flows from S to D, so VdsP is typically negative)
•VdsN = Drain to Source voltage of NMOS (current flows from D to S, so VdsN is positive)

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/77fac475-03bb-40c4-87e0-ed36902d9ba0" />
Fig 9: Complete voltage labelling — VgsP, VgsN, VdsP, VdsN shown on inverter circuit

These four voltage parameters — VgsP, VgsN, VdsP, VdsN — are what SPICE uses internally to determine the drain current flowing through each transistor at every point during a simulation. By tracking how these voltages change as Vin sweeps from 0 to Vdd, SPICE produces the VTC (Voltage Transfer Characteristic) curve that we analyse.

Drain Currents – IdsN and IdsP
Once the voltage parameters are defined, the next important quantities are the drain currents IdsN (NMOS drain current) and IdsP (PMOS drain current). From the figure below we can observe the current directions marked on both equivalent circuits.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/5bed3f23-2746-43f1-9b00-f92c90b2f779" />

Fig 10: Current directions — IdsN flowing through NMOS (Vin = Vdd case) and IdsP flowing through PMOS (Vin = 0 case)

when Vin=vdd
+ direct path exists between Vout and Vss,resulting Vout=0.

  
For the NMOS transistor when Vin = Vdd:
•IdsN flows from Drain (connected to Vout) to Source (connected to Vss = 0V)
•The load capacitor CL discharges through this current path, pulling Vout towards 0V
•This discharging speed depends on how large IdsN is, which depends on VgsN and W/L ratio of NMOS

For the PMOS transistor when Vin = 0V:
•IdsP flows from Source (connected to Vdd) through PMOS to Drain (connected to Vout)
•This charges the load capacitor CL, pulling Vout towards Vdd
•The charging speed depends on IdsP, which depends on VgsP and W/L ratio of PMOS
This is an extremely important concept for delay analysis. The delay of any CMOS circuit depends on how quickly CL can be charged or discharged. The faster the current IdsP or IdsN, the smaller the delay. This is why W/L ratio tuning directly impacts delay — by increasing the W/L of either transistor, we increase its drain current and therefore reduce the delay for that transition.

WHY is this understanding so important?
The behaviour studied in this lecture forms the physical foundation for everything that follows in CMOS design. 

Connection to Voltage Transfer Characteristic:
The VTC curve — which shows Vout vs Vin  is  a graphical representation of what we studied here. 
+ When Vin is LOW, Vout is HIGH (PMOS ON, NMOS OFF).
+ When Vin is HIGH, Vout is LOW (PMOS OFF, NMOS ON).
+ The transition between these two states in the middle region is where both transistors are partially ON, and that transition region determines noise margins, gain, and the shape of the VTC.

  <img width="868" height="344" alt="image" src="https://github.com/user-attachments/assets/f10a93a2-fd41-4b04-8973-2fc4085814fa" />

The naming of components is taken as below:
+ VgsN for gate voltage of NMOS
+ VgsP for gat voltage of PMOS.
+ In eqvivalent circuit Vin=Vdd,current is denoted as IdsN
+ For Vin=0,current is denoted as IdsP


Connection to DELAY
 As we know that delay depends on how fast the output node charges or discharges. That charging/discharging is done entirely by IdsP (when output goes HIGH) and IdsN (when output goes LOW). So the delay of the inverter directly depends on the drain currents, which in turn depend on VgsP, VgsN, VdsP, VdsN, and the W/L ratios — all of which we labelled in this lecture.



<head> PMOS/NMOS drain current v/s drain voltage </head>

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/6142ccec-2cb0-4fc9-a4ae-fbd6c15c7a14" />

From above picture we can observe the inverter circuit with all voltage parameters labelled.
VgsP,VgsN,VdsP,VdsN are the controlling voltages for PMOS and NMOS.
IdsP and IdsN are the drain currents of PMOS and NMOS respectively.
In this lecture we will find how IdsN changes with VdsN and how IdsP changes with VdsP.This is called Id vs Vds curve.

By Observation
From the inverter circuit we can directly find all the voltage expresions by observation.
The flow current is in opposite direction in circuits with Vin =Vdd and Vin = 0.
CMOS voltage characteristics comletely depends on Vin and Vout.

For NMOS:
Source of NMOS is connected to Vss = 0V.Gate of NMOS is connected to Vin.
So by observation:

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/d8dc3b11-2a2a-4df7-8222-b224fb80098a" />

VgsN = Vin - Vss = Vin - 0 = 'Vin'
Here Vss = 0 so VgsN simply equals Vin.
This means as Vin changes,VgsN changes by same amount.So we dont need to track both separately.

For VdsN:
Drain of NMOS is connected to Vout and Source is connected to Vss = 0V.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/ca30e246-64de-4fe2-bb63-74699b6a29f9" />

VdsN = Vout - Vss = Vout - 0 = 'Vout'
Here VdsN simply equals Vout.So as Vout changes,VdsN changes.

For PMOS:
Source of PMOS is connected to Vdd.Gate of PMOS is connected to Vin.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/2664c81f-14a4-47e2-b6f0-df817b2407ea" />

VgsP = Vin - Vdd = 'Vin - Vdd'
Here VgsP is always negative or zero because Vin is always less than or equal to Vdd.When Vin = 0 then VgsP = -Vdd which is most negative so PMOS is strongly ON.When Vin = Vdd then VgsP = 0 so PMOS is OFF.

VdsP = Vout - Vdd = 'Vout - Vdd'
VdsP is also always negative or zero because Vout is always less than or equal to Vdd.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/fa055513-9064-474f-bef7-091d82e282ed" />

By Observation:

IdsP = -IdsN

WHY IdsP = -IdsN?
From the circuit we can observe that PMOS and NMOS are sharing the same output node Vout.The current flowing through PMOS(IdsP) must be equal to current flowing through NMOS(IdsN) because they share same output node.There is no other current path.
The negative sign comes from sign convention diference between PMOS and NMOS.For NMOS,IdsN flows from Drain to Source.For PMOS,IdsP also flows from Drain to Source but in PMOS convention VdsP is negative so IdsP becomes negative.
So IdsP = -IdsN.This means we can derive PMOS curve from NMOS curve just by sign change.

NMOS IdsN Vs VdsN Curve

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/3ebde5af-b3e1-4a53-8606-f154f41432a0" />
From above picture we can observe that the  plotting is of  NMOS IdsN vs VdsN curve.

we know that NMOS has two operating regions:

•Linear Region: When VdsN <= VgsN - Vtn.Here current increases linearly with VdsN.
•Saturation Region: When VdsN > VgsN - Vtn.Here current becomes constant and does not depend on VdsN.

For each fixed value of VgsN we get one complete curve of IdsN vs VdsN.
As VgsN increases the curve sits higher meaning more current flows for same VdsN.This gives us a family of curves.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/184144b1-93d6-4389-8177-717be986c7c7" />

From above picture we can observe empty IdsN vs VdsN axes being set up.x-axis is VdsN and y-axis is IdsN.

Now curves are added one by one for each VgsN value.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/6dad12df-9b67-4e65-ae25-819dc0a3a79c" />

From above picture we can observe first two curves VgsN1 and VgsN2 appearing on the graph.
We can observe:
•At VdsN = 0: IdsN = 0.No current flows when there is no potential diference.
•As VdsN increases from 0: IdsN increases.This is linear region.
•After the pinch-off point where VdsN = VgsN - Vtn: IdsN becomes nearly constant.This is saturation region.
•VgsN2 > VgsN1 so curve for VgsN2 sits higher than VgsN1.More gate voltage means more current.

As we keep adding more curves for VgsN3,VgsN4,VgsN5 we observe:
•Each new curve sits higher than previous.
•The pinch-off point shifts to the right as VgsN increases.
•All curves start from origin(IdsN = 0 at VdsN = 0).
•In saturation region curves fan out as spacing increases with VgsN.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/129ed37f-a8d4-43d8-a1f4-cf7d03f280bc" />




From above picture we can observe complete NMOS IdsN vs VdsN family of curves with 5 curves for VgsN1 through VgsN5.
We can clearly observe linear region on left portion and saturation region on right flat portion for each curve.

Now connecting this back to our inverter:
We know VgsN = Vin and VdsN = Vout.So the NMOS curves are telling us:
•For a given Vin(= VgsN) how does IdsN change as Vout(= VdsN) varies.
•When Vout is large(close to Vdd): NMOS is in saturation.IdsN is approximately constant.CL discharges at constant rate.
•When Vout is small(close to 0): NMOS is in linear region.IdsN decreases as Vout decreases.Discharge slows down.
•Higher Vin means higher VgsN means larger IdsN means faster discharge means smaller tpHL delay.

PMOS IdsP Vs VdsP Curve
Now for PMOS.We already know that VgsP and VdsP are both negative quantities for properly operating PMOS.So when we plot IdsP vs VdsP both axes are in negative direction.
The instructor draws PMOS curve in a separate graph with x-axis pointing left(-VdsP) and y-axis pointing down(-IdsP).

WHY is PMOS graph in negative quadrant?
Because VgsP = Vin - Vdd and VdsP = Vout - Vdd.Since Vin and Vout are always between 0 and Vdd:
•VgsP ranges from -Vdd(when Vin = 0, PMOS fully ON) to 0(when Vin = Vdd, PMOS OFF).
•VdsP ranges from -Vdd(when Vout = 0) to 0(when Vout = Vdd).
Both are zero or negative.So the graph sits in third quadrant.To make it easy to read,instructor plots -VdsP on x-axis and -IdsP on y-axis so the curve appears as mirror of NMOS curve.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/81472547-ed87-4311-8b07-a505a78aa455" />

From above picture we can observe empty axes set up for PMOS IdsP vs VdsP curve.x-axis shows -VdsP pointing left and y-axis shows -IdsP pointing down.

Now PMOS curves are added one by one for each VgsP value.
For each value of VgsP(-VgsP1,-VgsP2,-VgsP3,-VgsP4,-VgsP5 all negative) we get one curve:
•-VgsP1 is smallest magnitude(VgsP closest to 0): PMOS just barely ON.Smallest current.
•-VgsP5 is largest magnitude(VgsP most negative): PMOS strongly ON.Largest current.
•Shape of each curve is same as NMOS: rises linearly then flattens into saturation.
•Curve with largest |VgsP| produces most current and sits furthest from origin.

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/a8d720a4-5b3e-4aba-8d2a-542f15ade902" />

From above picture we can observe complete PMOS IdsP vs VdsP family of curves with 5 curves for -VgsP1 through -VgsP5.These are plotted in negative quadrant mirroring the NMOS curves.

Connecting PMOS curve back to our inverter:
We know VgsP = Vin - Vdd and VdsP = Vout - Vdd.So PMOS curves are telling us:
•For a given Vin(which sets VgsP) how does IdsP change as Vout varies.
•When Vout is small(Vout close to 0): VdsP = -Vdd.PMOS is in saturation.IdsP is approximately constant.CL charges at constant rate.
•When Vout is large(Vout close to Vdd): VdsP close to 0.PMOS is in linear region.IdsP decreases.Charging slows down.
•Lower Vin means more negative VgsP means larger |IdsP| means faster charging means smaller tpLH delay.

NMOS and PMOS Curves Side by Side
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/9220f8a9-a23d-4bb2-8f86-2fa27baccf2c" />

From above picture we can observe both NMOS and PMOS Id vs Vds families plotted side by side.This is the final picture of this lecture.

From graphs we can observe:
For NMOS curve(left graph):
•x-axis is VdsN = Vout.
•y-axis is IdsN which is positive.
•Curves labelled VgsN1 through VgsN5 corresponds to 5 diferent values of Vin.
•Higher Vin means higher VgsN means larger IdsN means faster discharge of CL means smaller tpHL.

For PMOS curve(right graph):
•x-axis is -VdsP = Vdd - Vout.
•y-axis is -IdsP plotted as positive for clarity.
•Curves labelled -VgsP1 through -VgsP5 corresponds to 5 diferent values of Vin - Vdd.
•More negative VgsP means larger |IdsP| means faster charging of CL means smaller tpLH.

Since IdsP = -IdsN both families of curves are consistent with each other at every operating point.
In next lecture we will use both curves together on same plot to find operating point of inverter at each Vin value.The intersection of NMOS and PMOS curves at a given Vin gives us Vout at that point.By repeating this for all values of Vin from 0 to Vdd we get full VTC curve.

WHY?
These Id vs Vds curves are important because:

Connection to Delay:
The propagation delay tpHL and tpLH of any CMOS circuit depends on how quickly CL charges or discharges.The amount of current available at each operating point decides how fast voltage changes.
•Large IdsN at all Vout values means fast discharge means small tpHL.This is achieved by increasing W/L of NMOS.
•Large IdsP at all Vout values means fast charging means small tpLH.This is achieved by increasing W/L of PMOS.
•This is why delay tables in Liberty files(.lib) use W/L ratio as key parameter.The Id vs Vds curves shift with W/L.

Connection to SPICE:
When we run SPICE transient simulation of inverter:
•SPICE computes VgsN,VdsN,VgsP,VdsP at every time step using node voltages.
•It calculates IdsN and IdsP using model equations which describe exactly these Id vs Vds curves.
•It uses those currents to calculate dVout/dt = IdsN/CL for discharge and IdsP/CL for charge.
•Repeating for thousands of time steps gives complete Vout vs time waveform from which we measure delay.


Summary
Voltage Observations:
•VgsN = Vin
•VdsN = Vout
•VgsP = Vin - Vdd
•VdsP = Vout - Vdd

Current Observation:
•IdsP = -IdsN

NMOS IdsN vs VdsN Curve:
•One curve for each VgsN value(= one curve for each Vin value).
•Each curve shows linear rise then saturation plateau.
•Higher VgsN means higher IdsN means faster discharge means smaller tpHL.
•IdsN = 0 when VgsN < Vtn(NMOS in cutof).

PMOS IdsP vs VdsP Curve:
•One curve for each VgsP value(= one curve for each Vin - Vdd value).
•Plotted in negative quadrant.-VdsP on x-axis,-IdsP on y-axis.
•More negative VgsP means higher |IdsP| means faster charging means smaller tpLH.
•IdsP = 0 when VgsP > Vtp(PMOS in cutof,i.e Vin close to Vdd).


........................................................................................................................................................................................
# DAY 2.4

1. CMOS Inverter – Circuit Setup

<img width="893" height="509" alt="image" src="https://github.com/user-attachments/assets/c31b3b5d-8ea3-4fc2-8954-0da9f736bf15" />


Figure 1 – CMOS Inverter circuit with PMOS and NMOS I-V curve families
Before we get into the graphical analysis, 
we need to understand that the CMOS inverter circuit looks like.
we can understand realtion between terminal voltages Vin and Vout.

To get Voltage charcteristics which helps to find delay beacause these are function o Vin and Vot not Vss and Vdd.we have to gt rid of Vss and Vdd and convert it into required forms i.e Vin and Vout by taking IdsN current.We ind way to modiy into Vin and Vout as in real design we did not see Vss  and Vdd as these are inrternal voltages.we  will do this for static CMOS inverter.


Construction of the CMOS Inverter
The inverter has exactly 2 transistors:
•PMOS — source tied to Vdd, gate connected to Vin, drain at Vout
•NMOS — source tied to Vss (ground), gate connected to Vin, drain at Vout
A load capacitor CL sits at the output. This represents the input capacitance of the next gates being driven.

The push-pull arrangement means when one transistor turns ON, the other turns OFF. This is what gives CMOS its very low static power — in steady state there is no DC path from Vdd to Vss.

Voltage Relationships — By Observation
By just looking at the circuit (using KVL on simple loops), we can write the terminal voltages of both transistors in terms of Vin and Vout. These hold regardless of which operating region the transistors are in:

For the NMOS (source at Vss = 0):
VgsN = Vin - Vss = Vin
VdsN = Vout - Vss = Vout

For the PMOS (source at Vdd):
VgsP = Vin - Vdd
VdsP = Vout - Vdd

These are simple but very powerful. VgsN is literally just Vin. VdsN is literally just Vout. For PMOS both are shifted by Vdd because its source floats at Vdd instead of ground.

The KCL Constraint — What Pins the Operating Point
At the output node, current flowing in from PMOS must equal current flowing out into NMOS. So:

IdsP = − IdsN

The negative sign is from sign convention — IdsN flows downward through NMOS (drain to source), while IdsP flows upward from the output into the PMOS drain. They are equal in magnitude but opposite in sign.

This constraint is the key to the whole graphical method. The actual Vout for any given Vin is the voltage where NMOS current = PMOS current in magnitude. Wherever the two transistors' I-V curves intersect on the same plot — that is the operating point.

2. NMOS and PMOS I-V Characteristics

   <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/24ee3205-5d53-4aae-8eff-3b574e5d55e3" />

Figure 2 – NMOS IdsN vs VdsN (left) and PMOS IdsP vs VdsP (right) characteristic curves 
NMOS Characteristics: IdsN vs VdsN
The left chart shows 5 families of curves for VgsN1 through VgsN5 (increasing from bottom to top). Each curve shows 2 regions of behaviour:

•Triode/Linear region — when VdsN < VgsN - Vtn, current rises steeply with VdsN. The transistor acts like a resistor here.
•Saturation region — when VdsN >= VgsN - Vtn, current flattens and becomes nearly constant. The transistor acts like a current source.

Since VgsN = Vin and VdsN = Vout, each curve on this plot directly tells us: for a given Vin (which selects the curve), how much NMOS current flows as a function of Vout.

PMOS Characteristics: IdsP vs VdsP
The right chart shows the PMOS family in the third quadrant — both VgsP and VdsP are negative in normal PMOS operation. Curves are labeled -VgsP1 through -VgsP5 where -VgsP5 is most negative (PMOS fully ON, most current).

These PMOS curves cannot simply be pasted on top of the NMOS plot. We need two transformations:
+Mirror vertically — because IdsP = -IdsN, we need to flip the PMOS current axis upward
+Shift horizontally — because VdsP = Vout - Vdd, the PMOS curve origin (VdsP=0) maps to Vout = Vdd on the x-axis

After these two operations the PMOS curves become load lines that can be overlaid directly on the NMOS IdsN vs Vout plot.

3. Mapping VgsP to Vin — The Key Bridge
<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/3efb0982-8edb-4533-8a27-125950a9a040" />

Since VgsP = Vin - Vdd, we can rearrange to get:

Vin = VgsP + Vdd

This is the bridge between the PMOS curves (which are labeled in VgsP) and the inverter input voltage Vin. Once we do this mapping, we can relabel the PMOS curves using Vin directly — making them directly comparable with NMOS curves which are already labeled in Vin (since VgsN = Vin).

The Mapping Table (Vdd = 2V)
For Vdd = 2V, the mapping is:

+  Vgsp1 = 0 V      →   Vin = 0 + 2 = 2.0 V   (PMOS barely ON)
+  Vgsp2 = -0.5 V   →   Vin = -0.5 + 2 = 1.5 V
+  Vgsp3 = -1.0 V   →   Vin = -1.0 + 2 = 1.0 V  (transition region)
+ Vgsp4 = -1.5 V   →   Vin = -1.5 + 2 = 0.5 V
+ Vgsp5 = -2.0 V   →   Vin = -2.0 + 2 = 0.0 V  (PMOS fully ON)

Physical Meaning of the Mapping
This mapping confirms the inverter behavior from the PMOS side:

When Vin = 0: VgsP = -2V. PMOS has large negative gate-source voltage — it is strongly ON and pulls output toward Vdd. Output is HIGH. This is correct inverter behavior for LOW input.

When Vin = 2V (= Vdd): VgsP = 0V. PMOS gate and source are at same potential — it is OFF. NMOS is strongly ON and pulls output to Vss. Output is LOW. Correct behavior for HIGH input.

When Vin = 0.5 V, 1.0 V, 1.5 V: Both transistors conduct simultaneously. This simultaneous conduction in the transition region is what creates the steep, high-gain transition in the Voltahr Characteristics Curve. It also causes a brief current spike (short-circuit current) during switching,this is a source of dynamic power loss.

4. Superimposing PMOS Load Lines on NMOS Plot

   <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/410fcce1-0928-4861-8798-63b6f77f6d9a" />

   Figure 4 – PMOS curves relabeled with Vin values and overlaid on the NMOS plot (~3:00)
After relabeling PMOS curves with Vin values, they are overlaid onto the NMOS IdsN vs Vout chart. To do this correctly we need 2 transformation steps:

Step 1 — Mirror Vertically (Negate Current)
Because IdsP = -IdsN, we plot -IdsP on the IdsN axis. This flips the PMOS curves upside down — curves that went negative now go positive, consistent with the IdsN axis direction. The PMOS starts supplying current (plotted upward) where Vout is near Vdd, and drops to zero as Vout approaches 0.

Step 2 — Shift Horizontally (Change Voltage Reference)
The PMOS curves are plotted against VdsP = Vout - Vdd. When VdsP = 0, Vout = Vdd = 2V. When VdsP = -Vdd = -2V, Vout = 0V. So the PMOS load line origin maps to the right edge (Vout = Vdd) of the plot, and the curve runs leftward toward Vout = 0. The PMOS curves run right-to-left on the Vout axis because VdsP becomes more negative as Vout decreases.

The Resulting Load Lines
After these transformations each PMOS curve becomes a load line on the IdsN vs Vout plot:
•Vin = 0 (PMOS most ON) → highest load line, most current available
•Vin = 2 (PMOS barely ON) → lowest load line, nearly zero current

These load lines are analogous to the resistive load lines used in BJT amplifier analysis. The difference here is that they are curved (not straight) because the PMOS follows its I-V characteristic, not a linear V=IR relationship.

5. Finding Operating Points and Building the VTC
  <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/fbf4e86f-3cd7-4ac2-8127-84711d5c1018" />

Figure 5 – NMOS curves and PMOS load lines overlaid; intersection points are operating points 
For each value of Vin, there is exactly one intersection between the corresponding NMOS curve and PMOS load line. This is guaranteed because NMOS current increases with Vout (for fixed Vin) while PMOS load line decreases with Vout — two monotone curves in opposite directions must cross exactly once.

Reading the 5 Operating Points
Reading the Vout at each intersection gives:

• Vin = 0.0 V   →  Vout ≈ 2.0 V (Vdd)   NMOS OFF, PMOS fully ON, output HIGH
• Vin = 0.5 V   →  Vout ≈ 1.8 V           NMOS barely ON, PMOS strongly ON
• Vin = 1.0 V   →  Vout ≈ 1.0 V           Both partially ON, transition region
• Vin = 1.5 V   →  Vout ≈ 0.2 V           NMOS strongly ON, PMOS barely ON
• Vin = 2.0 V   →  Vout ≈ 0.0 V (Vss)   NMOS fully ON, PMOS OFF, output LOW

Building the VTC from These Points
Plotting these 5 (Vin, Vout) pairs on a graph with Vin on x-axis and Vout on y-axis gives the Voltage Transfer Characteristic (VTC). Connecting these 5 points smoothly gives the S-shaped VTC curve:
•For low Vin (0 to ~Vtn): Vout stays near Vdd — output is held HIGH
•Around Vm (≈ Vdd/2 = 1V): Vout drops sharply — this is the high-gain transition region
•For high Vin (near Vdd): Vout stays near 0 — output is LOW

The steepness of the VTC transition (gain = dVout/dVin in the transition region) determines the noise margins of the gate. The steeper the better — more noise rejection.

Switching Threshold Vm: It is defined as the Vin value where Vout = Vin (VTC crosses the unity-gain line). For a perfectly symmetric inverter Vm ≈ Vdd/2. In practice Vm is tuned by sizing the W/L ratio of PMOS vs NMOS. Increasing PMOS width shifts Vm higher, increasing NMOS width shifts Vm lower.

6. Final Combined Plot and Key Takeaways

 <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/1c96a7c0-5cf8-4d34-99bb-55d8379f50e1" />


The final combined plot shows all 5 NMOS curves and 5 PMOS load lines overlaid on a single set of axes. Each NMOS curve and its corresponding PMOS load line share the same Vin label, and they intersect at exactly one point each. These 5 intersection points are the operating points of the inverter.

What We Can Read from This Plot
The combined plot is very information dense. From it we can observe:
•Where curves cross at steep angles → high gain → sharp VTC transition
•Where curves cross nearly parallel → low gain → gradual transition
•NMOS OFF + PMOS fully ON (Vin = 0) → intersection at Vout = Vdd
•NMOS fully ON + PMOS OFF (Vin = Vdd) → intersection at Vout = 0
•In the middle (Vin ≈ Vdd/2) → both partially ON → intersection near Vdd/2 → inverter is in transition

Why This Graphical Method is Important
This method gives us physical intuition that algebraic solutions can't easily provide. We can answer questions like:

+If Vdd is reduced, how does the VTC shift? — Curves compress, Vm shifts, noise margins shrink
+If PMOS width is doubled, what happens? — PMOS curves shift up, more current, Vm increases
+If Vtn increases (process variation), what changes? — NMOS curves shift, Vm shifts downward.






.........................................................................................

# Lecture 25

L5 – Step 3: Converting I-V Curves to Load Curves

<img width="884" height="475" alt="image" src="https://github.com/user-attachments/assets/3bd9f35e-4707-4b38-bcf9-cb9a9c484e3a" />

Figure 1 – Recap slide: PMOS curves relabelled with Vin values, VgsP-to-Vin table, and observation equations.

we done step 1 where we converted VgsP as a function of Vin.
Next VdsP as a function as Vout.


The goal here is to convert both the PMOS and NMOS I-V curves from their original terminal voltage axes (VdsP and VdsN) to the Vout axis. Once both sets of curves are on the same Vout axis, we can overlay them and find the operating point of the inverter for each Vin.

Step 1 — Converting PMOS Curves to Vout Axis

<img width="873" height="464" alt="image" src="https://github.com/user-attachments/assets/4222c1e3-3b95-45b5-9f4d-0154aef2792c" />

Figure 2 – PMOS curves (left) being transformed to IdsN vs Vout axes (right) using Vout = Vdd + VdsP (~2:03)
The Conversion Formula
By observation from the circuit, VdsP = Vout - Vdd. Rearranging gives:

Vout = Vdd + VdsP

This formula lets us swap the x-axis of the PMOS plot from VdsP to Vout. Every point on the PMOS curves can now be expressed in terms of Vout.

How the x-axis changes
Before the substitution, the PMOS x-axis ran from VdsP = 0 (at the right) to VdsP = -Vdd (at the left). After the substitution:
•VdsP = 0     →   Vout = Vdd + 0 = 2 V   (right side of the new plot)
•VdsP = -Vdd  →   Vout = Vdd - Vdd = 0 V  (left side of the new plot)

when Vout becomes 2V,At Vout = 2V the current is Zero which states output capacitor is ully charged and no charging current lows through it.so,it Vout=2V eventhogh we vary Vdd.

So the new Vout axis runs from 0 V (left) to 2 V (right). The PMOS curves, which ran right-to-left in VdsP, now naturally run right-to-left in Vout too — starting at high Vout near Vdd and falling toward Vout = 0.

How the y-axis changes
The original PMOS y-axis showed IdsP which is negative in normal operation. But since IdsP = -IdsN, we flip the y-axis:

IdsN (plotted) = -IdsP

This flips the curves vertically. Curves that originally pointed downward now point upward in the new IdsN vs Vout coordinate system.

Result of the PMOS transformation
The PMOS load curves now look like this on the IdsN vs Vout axes:
•Vin = 0  →  top curve  (PMOS fully ON, maximum current delivered to output)
•Vin = 0.5  →  second curve
•Vin = 1  →  middle curve
•Vin = 1.5  →  fourth curve
•Vin = 2  →  bottom curve  (PMOS barely ON, nearly zero current)

All curves start at the right (Vout near Vdd) and fall as Vout moves left toward 0. This is the opposite direction compared to NMOS curves  which rise from the left. That opposing shape is exactly what allows them to intersect and define an operating point.

Step 2 — The Final PMOS Load Curve
<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/b02d0f6c-9f76-4efd-b612-ac3ad29a2c7a" />


Figure 3 – Three-stage derivation of PMOS load curve: original VdsP plot → Vin relabelling → Vout axis (~3:33)
The full transformation from the original PMOS I-V plot to the final load curve is a 2-step process:

Step 1: Relabel VgsP curves with Vin values using Vin = VgsP + Vdd (done in L4)
Step 2: Substitute Vout = Vdd + VdsP on the x-axis and flip the y-axis from IdsP to IdsN = -IdsP

After both steps, the PMOS load curve plot shows IdsN vs Vout for each Vin. This is what the instructor labels as the 'Load Curve for PMOS transistor'.

Physical meaning of PMOS load curve shape
When Vout is near Vdd: VdsP = Vout - Vdd ≈ 0. PMOS drain and source are at similar voltages. PMOS is in saturation — delivering steady current.

When Vout falls toward 0: VdsP becomes more negative (= Vout - Vdd). Eventually PMOS enters linear/triode region and current drops.

When Vout = 0: VdsP = 0 - Vdd = -Vdd = -2 V. PMOS is deep in linear region. For the Vin = 2 curve (PMOS barely ON), current here is essentially zero. For the Vin = 0 curve (PMOS fully ON), there is still some current.

Step 3 — Converting NMOS Curves to Vout Axis

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/05fad1cf-3ce5-4927-99ac-a071ef7897ae" />
Figure 4 – PMOS load curve (right) now complete; NMOS conversion about to begin (~5:03)
The NMOS conversion is simpler than PMOS. By observation:

VgsN = Vin    and    VdsN = Vout

Because VdsN = Vout directly (no shift needed), we just relabel the x-axis of the NMOS plot from VdsN to Vout. No adding Vdd, no axis flipping.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/f88ffa6d-ecf6-4d31-86eb-85806a2e7423" />

Figure 5 – Slide showing the NMOS load curve being derived from the NMOS IdsN vs VdsN curves using VgsN = Vin and VdsN = Vout (~6:33)
NMOS Load Curve Derivation
The slide shows: 'Let us obtain the Load Curve for NMOS transistor using the above equations.'

The NMOS I-V curves are originally labeled VgsN1 through VgsN5. Since VgsN = Vin, we can directly relabel them:

•VgsN1 = 0   →   Vin = 0   (NMOS OFF — below threshold, IdsN ≈ 0)
•VgsN2 = 0.5 →   Vin = 0.5
•VgsN3 = 1   →   Vin = 1
•VgsN4 = 1.5 →   Vin = 1.5
•VgsN5 = 2   →   Vin = 2   (NMOS fully ON — maximum current)

And the x-axis VdsN is directly replaced with Vout since VdsN = Vout. No other changes needed.

Result of the NMOS transformation
The NMOS load curves on IdsN vs Vout axes:
•Vin = 0  →  bottom curve  (NMOS OFF, no current for any Vout)
•Vin = 0.5, 1, 1.5  →  intermediate curves rising in that order
•Vin = 2  →  top curve  (NMOS fully ON, rises steeply then saturates)

The NMOS curves rise from left to right — from low Vout toward high Vout. This is the opposite of the PMOS load curves which fall from right to left. That opposite orientation is what causes them to cross.

Step 4 — Both Load Curves Ready for Merging

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/dcd77bcd-0fc5-4c90-8e53-71b0b05c5c3c" />

Figure 6 – Final slide showing NMOS load curves (centre) and PMOS load curves (right) on the same Vout axis, ready to overlay (~8:48)
At the end of this lecture, both sets of load curves are available on the same coordinate system: IdsN on the y-axis, Vout on the x-axis.

Comparison of the two load curve sets
•NMOS load curves:  rise left-to-right (low Vout → high Vout). Vin = 0 at bottom, Vin = 2 at top.
•PMOS load curves:  fall right-to-left (high Vout → low Vout). Vin = 0 at top, Vin = 2 at bottom.

For any given Vin, the NMOS curve and PMOS load curve run in opposite directions on the same Vout axis. They must cross exactly once. That crossing point is the DC operating point of the inverter for that Vin — it gives the steady-state Vout.

WHY does this work?
The operating point is the condition where IdsP = -IdsN (KCL at the output node). Since we converted both curves to the IdsN axis, the operating point is wherever the NMOS IdsN curve and the PMOS load curve (which is already -IdsP = IdsN) are equal. That is simply where they intersect.

Summary — Key Equations from This Lecture
•Vout = Vdd + VdsP                    [PMOS x-axis substitution]
•IdsN plotted = -IdsP                  [PMOS y-axis flip]
•VdsN = Vout                           [NMOS x-axis substitution, direct]
•VgsN = Vin                            [NMOS curve relabelling]
•Vin = VgsP + Vdd                      [PMOS curve relabelling, from L4]
•IdsP = -IdsN                          [KCL constraint at output node]

.............................................................................................

# Lecture 26

Step 4 — Merging Load Curves and Building the VTC.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/f4493837-aa47-4a0a-9ec3-91b64817bbb7" />

Figure 1 – Both load curves side by side. 
+ Centre: NMOS load curve (Vin = 0 bottom, Vin = 2 top). 
+ Right: PMOS load curve (Vin = 0 top, Vin = 2 bottom). VTC axes empty at bottom right.
In the previous lecture (L5) we converted both the PMOS and NMOS I-V curves into load curves on the same IdsN vs Vout axes. Now we merge them onto a single plot and read the operating points.

The idea is simple:
•For each Vin, there is one NMOS load curve and one PMOS load curve active simultaneously.
•They intersect at exactly one point — that is the DC operating point of the inverter for that Vin.
•Reading Vout at each intersection and plotting (Vin, Vout) builds the Voltage Transfer Characteristic (VTC).

Step 1 — Superimposing Both Load Curves


<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/9015dc1d-3d50-4139-9a48-dcde769283fc" />

Figure 2 – NMOS and PMOS load curves merged on one IdsN vs Vout plot. PMOS runs top-right to bottom-left, NMOS runs bottom-left to top-right.

From observation, Vin and Vout are common to both transistors  the same Vin drives both gates, and the same Vout appears at both drains. So for a given Vin:

+  PMOS load curve is active (selected by that Vin value)
+  NMOS load curve is active (selected by that same Vin value)
•The intersection satisfies IdsP = -IdsN, which is the KCL constraint at the output node

+ Vin and Vout are common to PMOS and NMOS. Graphically, we will pick up Vin points from the intersection of corresponding load lines.

WHY do they cross exactly once?
The NMOS load curve rises from left to right (current increases as Vout increases, for fixed Vin). The PMOS load curve falls from right to left (current decreases as Vout decreases from Vdd). They are monotone in opposite directions — so they must cross exactly once. That crossing is the unique stable operating point.

Step 2 — Reading All 5 Operating Points

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/e8200a0f-ad03-4e9a-ad42-52f27a619f62" />

Figure 3 – First intersection point marked: When Vin = 0, Vout = 2 V. VTC dot plotted at (0, 2). PMOS linear, NMOS off (~1:40–2:30)
Operating Point 1 — Vin = 0 V
•NMOS:  VgsN = 0 V → below threshold → NMOS is OFF → IdsN = 0 for all Vout
•PMOS:  VgsP = 0 - 2 = -2 V → strongly ON → maximum current
•Intersection:  NMOS IdsN = 0 and PMOS at Vin = 0 cross at Vout = 2 V (= Vdd)
•Region:  PMOS linear, NMOS off
•Physical meaning:  NMOS pulls no current to ground. PMOS pulls output all the way to Vdd. Output is HIGH.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/7003fc21-a4af-4dbc-adc1-24f9826552f6" />

Figure 4 – Second intersection point: When Vin = 0.5, 1.5 < Vout < 2. VTC dot 
Operating Point 2 — Vin = 0.5 V
+ NMOS:  VgsN = 0.5 V → slightly above threshold → NMOS barely ON → small IdsN
+ PMOS:  VgsP = 0.5 - 2 = -1.5 V , still strongly ON
+ Intersection:  Occurs at Vout between 1.5 V and 2 V — approximately 1.9 V
+ Region:  PMOS linear, NMOS saturation
+ Physical meaning:  PMOS still dominates and holds output near Vdd. NMOS starts to pull down slightly.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/def7cd6d-e138-4254-8666-795bddd29ef5" />

Figure 5 – Third intersection point: When Vin = 1, 0.5 < Vout < 1.5. VTC dot. PMOS sat, NMOS sat. VTC now showing steep fall.

Operating Point 3 — Vin = 1 V (Transition Region)
+ NMOS:  VgsN = 1 V → moderately ON
+ PMOS:  VgsP = 1 - 2 = -1 V → moderately ON
+ Intersection:  Occurs near Vout = 1 V — the midpoint
+ Region:  PMOS saturation, NMOS saturation
+ Physical meaning:  Both transistors are simultaneously conducting in saturation. This is the highest-gain region of the inverter. A small change in Vin produces a large change in Vout here.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/dd0253b7-88c7-48bc-91d5-2693d3dc9651" />

Figure 6 – Fourth intersection point: When Vin = 1.5, 0 < Vout < 0.5. VTC dot. PMOS sat, NMOS linear.
Operating Point 4 — Vin = 1.5 V
•NMOS:  VgsN = 1.5 V → strongly ON → in linear region for this Vout range
•PMOS:  VgsP = 1.5 - 2 = -0.5 V → barely ON → in saturation
•Intersection:  Occurs at Vout between 0 V and 0.5 V — approximately 0.1 V
•Region:  PMOS saturation, NMOS linear
•Physical meaning:  NMOS now dominates and pulls output close to ground. PMOS barely contributes.

Operating Point 5 — Vin = 2 V
•NMOS:  VgsN = 2 V → fully ON → in linear region
•PMOS:  VgsP = 2 - 2 = 0 V → OFF (gate = source voltage, no channel)
•Intersection:  PMOS Vin = 2 load curve delivers zero current. NMOS Vin = 2 curve intersects at Vout = 0 V
•Region:  PMOS off, NMOS linear
•Physical meaning:  PMOS is completely off. NMOS pulls output all the way to Vss = 0 V. Output is LOW.

Step 3 — The Complete VTC

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/c7f462e0-dc0f-407c-af1d-33d7c3557e0d" />

Figure 7 – Complete VTC with all 5 operating points plotted and connected. Each point labeled with transistor regions. The S-shaped VTC is now fully derived.
Plotting the 5 operating points on the Vout vs Vin graph and connecting them gives the complete Voltage Transfer Characteristic (VTC) of the CMOS inverter.

# Summary table of all 5 operating points
+ Vin = 0.0 V  →  Vout = 2.0 V   , PMOS linear,  NMOS off
+ Vin = 0.5 V  →  Vout ≈ 1.9 V  ,  PMOS linear,  NMOS saturation
+ Vin = 1.0 V  →  Vout ≈ 1.0 V  ,  PMOS sat,     NMOS saturation  ← transition region
+ Vin = 1.5 V  →  Vout ≈ 0.1 V  ,  PMOS sat,     NMOS linear
+ Vin = 2.0 V  →  Vout = 0.0 V  ,  PMOS off,     NMOS linear

What we can observe from the VTC shape
Low Vin region (0 to ~0.5 V):  Vout stays near Vdd = 2 V. Output is HIGH. PMOS dominates.

Transition region (~0.5 to ~1.5 V):  Vout drops steeply from 2 V to 0 V. Both transistors conduct simultaneously. This is the high-gain region of the inverter. The VTC is steepest here.

High Vin region (1.5 to 2 V):  Vout stays near 0 V. Output is LOW. NMOS dominates.

WHY is the transition region steep?
In the transition region, both PMOS and NMOS are in saturation simultaneously. In saturation, both act as current sources — one pushing current in and one pulling current out. A tiny change in Vin upsets this balance significantly, causing a large shift in Vout. This is why the gain dVout/dVin is very large (and negative) in this region, and why the VTC transition is sharp.

The steeper the VTC transition, the higher the noise margin of the gate. CMOS inverters have a very sharp transition, which is one reason they are preferred over other logic families.

5 Operating Regions of the CMOS Inverter
•Region 1 — PMOS linear, NMOS off           (Vin near 0)
•Region 2 — PMOS linear, NMOS saturation    (Vin slightly above Vtn)
•Region 3 — PMOS saturation, NMOS sat       (Vin near Vdd/2) — highest gain
•Region 4 — PMOS saturation, NMOS linear    (Vin slightly below Vdd)
•Region 5 — PMOS off, NMOS linear           (Vin near Vdd)

These 5 regions correspond exactly to the 5 segments of the VTC curve. They will be analysed in detail in the next lecture when we formally define noise margins, switching threshold Vm, VOH, VOL, VIH, and VIL.

# DAY 2.6

............................................................................................

# DAY 3.1

<b> SPICE SIMLATIONS </b>

   # SPice Deck
   + it is the connectivity inormation about a netlist such as:
    + Tap points where we take output.
    + Connectivity information.
    + Input parameters that need to be provided.

     <img width="451" height="380" alt="image" src="https://github.com/user-attachments/assets/577e6aef-679e-4701-8b29-26cfb3b0bda3" />.

+ Here we create spice deck for complete netlist.We have PMOS which denoted by using arrows rather than Dot at gate.likewise we are diferentiating PMOS and NMOS by direction of arrows.
+ we deine connectivity of  substrate.It is potential component on PMOS and NMOS.
+ so we nee dto define its connectivity.
+ We need to see  bias of Substarte which can tune threshold voltage.

Connections:       
+ source of PMOS connected to Vdd.
+ source of NMOS is connected to Vss.
+ WE have input voltage an doutput load capacitance which depends on many parameters.
+ we assueme it as 10emto farads.

Deine Component Values:

<img width="419" height="376" alt="image" src="https://github.com/user-attachments/assets/30ae19f8-a5a3-4439-ac16-cea900daeb2a" />

+ PMOS W=0.375u,L=0.25u.
+ NMOS W=0.375,L=0.25u.
+ Cload=10fF.,
+ PMOS should be wider than NMOS.(ideally)
+ input gate voltage as 2.5V.
+ Assume drain voltage/Supply Voltage 2.5V. 
+ Connect common Vss.

   
# Identiy 'NODES'

<img width="486" height="403" alt="image" src="https://github.com/user-attachments/assets/022f2f91-f509-4505-85d0-74fbb81ee1ec" />

+ M1 is deined between 3 nodes.
+ Load capacitor defined btween 2 nodes.
+ These deined Spice Netlist.
+ We kep names to Nodes as 0,in,out.

Netlist Description

<img width="457" height="103" alt="image" src="https://github.com/user-attachments/assets/c9fc1f20-3c75-4704-88d9-941b09a708e7" />

Drain,gate,source,substrate order of syntax for nodes as M1
+ Drain is connected to out.
+ Gate is connected to Vin.
+ Substrate is connected to Vdd
+ Source is connected to Vdd.
+ Type is PMOS.
+ W=0.375
+ L=0.25
Similarly to M2

# Day 3.2

<img width="410" height="358" alt="image" src="https://github.com/user-attachments/assets/8a0f749e-1713-4703-966a-4a774be38e18" />

+ M2 as NMOS,it is connected in formm of Drain,gate source substrate.
+ Other parameters such as capaitor load as 10fF connected between out and o.
+ Vdd as 2.5V connected between vdd and 0
+ Vin as 2.5V connected between in and 0.

<img width="820" height="355" alt="image" src="https://github.com/user-attachments/assets/d99b51ea-5c3d-4302-9036-0744d81d8f6b" />


  Simulation commands

  + sweep gate input voltage rom o,2.5 at steps o 50mv and measuring outpt waveform.
  + inally we need to upload MODEL ile where it takes prameters of NMOS,PMOS.

#   SIMULATION(3.2,3.3)




................................................................................

# DAY 3.2.1

 # Switchinh Threshold.

 <img width="477" height="383" alt="image" src="https://github.com/user-attachments/assets/79c621e8-015c-4986-b44d-9e939b36a5bf" />

 Analysing the SPICE wavefrom or graph that we simulated.


 <img width="1843" height="860" alt="image" src="https://github.com/user-attachments/assets/3be3b82d-25cc-4e51-89fa-7ef057168f00" />



we are comparing 2 waveform with diferent parameters as given Wn=0.375u,Ln,p+0,25u and Wn=0.375u,Wp=0.9375u,Lnn,p=0.25u.
+ the shapes of waveforms are almost same.This states that CMOS inverter is Robust.
+ Vin is high output is 0,Vin is low output is 0.

1) Switching Threshold(Vm):The point at which the device switches.
2) Noise margin
    The above states characteristics of device.

SWitching threshold Vin = Vout

<img width="1834" height="667" alt="image" src="https://github.com/user-attachments/assets/332947aa-ce41-495b-a51f-12d9aa65ee0a" />

<img width="798" height="428" alt="image" src="https://github.com/user-attachments/assets/685edbac-1492-4321-bdeb-bf95f7a4a34b" />


+ By drawing a ine o tan45 we will find a point where line intersects Graph.The intersection point is switching threshold Voltage.(0.9)

+ For bigger width we observe switching threshold at 1.2V

+ At switching point both CMOS and NMOS are at saturation point states taht both are turned ON.
+ This results in chances of leakage of current.
+ In two regions either o the devics is of,so there is no current lows from power to ground except at Vm.


<img width="762" height="365" alt="image" src="https://github.com/user-attachments/assets/cf2d72aa-8873-438a-b034-c283d68343ec" />

+ Case 1:
   + When Vin = Vout,gate voltage Vgs = Vds drain voltage Vgs>>Vt.
   + At this point current magnitude in both PMS and NMOS is same but direction is opposite.
   + IdsP=-IdsN,same magnitude but diferent direction.

.....................................................................................
# 3.2.2

<img width="851" height="430" alt="image" src="https://github.com/user-attachments/assets/154a47a1-46a0-40f2-90ec-f7bd2dd7d42c" />

Vm is point where output switches.We are analysing for 2 conditions.we are evaluationg analytical behavior.

<img width="641" height="315" alt="image" src="https://github.com/user-attachments/assets/8859770c-adb6-486e-bfe8-e0342af3f94e" />

 We are  checking where NMOS and PMOS lies in Velocity saturation region.
 Vds=Vgs - Vt as Vt is small
 we get Vds = Vgs.

 <img width="752" height="324" alt="image" src="https://github.com/user-attachments/assets/8a7f0e78-e6b0-41d8-a299-cca93f422cae" />
  By kirchof law we get equation shown in above picture.It shows there is complete dependency of Vm on IdsN and IdsP.we solve IdsP,IdsN to get value of Vm.

1)we define value of Vm by W,L values:
   <img width="413" height="97" alt="image" src="https://github.com/user-attachments/assets/9511d679-2791-47ee-a34c-ae2e5d0a35e4" />

   + Drain current value equation is shown above.
   + Vdsat  is saturation voltage value
   +  ignore Lamba  for derivtio a sit is nearlly equalt to 0.
   +  we have 2 values of Vgs:
    + one for PMOS.
    + one for NMOS.
      
<img width="316" height="78" alt="image" src="https://github.com/user-attachments/assets/5297dd0d-be20-42e4-90e0-4fe22fb95913" />

NMOS for drain currwnt is in terms IdsN,Kn
VgsN=Vm,Vt

<img width="809" height="327" alt="image" src="https://github.com/user-attachments/assets/ac6bdc68-e5e5-4131-b5a4-1261122c454f" />


similarly we dit it for PMOS:
 Vin = Vout evalluating at this point.
 Vgsp= Vm-Vdd
 Vm=Vin=Vout      

 These are values o drain current.

 we will solve  Idsn and Idsp by equating it to zero.

   <img width="110" height="37" alt="image" src="https://github.com/user-attachments/assets/82628589-4f01-498e-869e-37bb4a917ff6" />

   solving the equation

   <img width="1486" height="1155" alt="image" src="https://github.com/user-attachments/assets/3695e978-7c12-4540-83db-a54e8c5bdf39" />

   where R is    <img width="215" height="58" alt="image" src="https://github.com/user-attachments/assets/7765212b-e555-4d5c-a965-878075acebd4" />
R is constant.Thi is known a sProcess transconductance.
+ It si a gain factor.
+ Kp is function of Wp/Lp
+ Kn is unation of Wn/Ln

  we get all parmetric values rom Model files and we we get value of R.
  from that we will get value of Vm.


# lecture 3.2.3

 Case 2:  We try to set value of Vm and evaluate  W/L values of both NMOS and PMOS.  

  <img width="831" height="339" alt="image" src="https://github.com/user-attachments/assets/44ed4957-db0f-421d-8bb6-44810651a491" />


  + set value of Vm.let assume power supply is 2.5V
  + To switch transsistors exactly at Half of  power supply i.e 1.25V
    + To  satisy above condition what should be value of W/L ratio of PMOS and NMOS.

Expression remains same by subjecting W/L values in terms of Vm for both PMOS and NMOS.
Application for this is when we have operation of clock tree with some predefined targets o Vm then we need to tune W/L ratio of PMOS and NMOS to get required results.

Derivation:

<img width="1920" height="1449" alt="image" src="https://github.com/user-attachments/assets/b73642e9-0f6d-4525-b2e1-b65676c352a9" />

+ equation states about the diference in ratios of W/L ration PMOS and NMOS completely depnding on single variable which is Vm.

# Lecture 3.2.4(SIMULATION)

<img width="812" height="460" alt="image" src="https://github.com/user-attachments/assets/4376ed47-da85-4076-b761-b6b38fef02ac" />

 Here we are going to find the value so SWITCHNG THRESHOLD by varying W/L ratios of NMOS.
  we did our SPICE simlation.


<img width="1227" height="907" alt="image" src="https://github.com/user-attachments/assets/c2b0f993-4508-443c-bac5-4bf76bab72c6" />

 To calculate switching threshold we will draw a line with slope 1 and find intersection point.This is Vm.
 + From this we can ind dynamic simulation such as Rise and Fall delay.we identify what is Rsie and All and how doe sit vary with Vm.
 + everything is same,we just change input to Pulse.This is known as Transient analysis.

Pulse:

 <img width="775" height="338" alt="image" src="https://github.com/user-attachments/assets/757be93e-94c0-4d1a-86e2-7f0922fdf5c2" />

 + Pulse starts rom Zero and ends at 2.5V with shit value zero.
 + starts exactly ar=t time unit 0.
 + rise time of 10ps and fall time of 10ps.
 + complete cycle of 2ns with duty cycle of 1ns.

   Results:

   <img width="759" height="473" alt="image" src="https://github.com/user-attachments/assets/a68893f0-2cb5-4913-ba64-936f1753ab25" />


   we can find rise delay from graph.
   + Rise delay is difference between Vin at falling edge and Vout at raising point exactly at midpoint..
   + similarly for fall delay.It is dierence between the Voltage at raising of Vin and  falling of Vout exactly at 50% value of Vin i.e 1.25V.

     <img width="759" height="389" alt="image" src="https://github.com/user-attachments/assets/8e1b0b31-f35e-475f-b23d-59e1a0fa61bc" />

+ For given values of Kp,Kn,the rise delay is 148ps and fall delay is 71ps for Vm=0.99V.

  # Lecture 3.2.5(SIMULATIONS)





  # Lecture 3.2.6

  Until now we found Rise Delay,Fall Delay for diferent value of W/L ratios of PMOS and NMOS.By varying PMOS size w.r.t NMOS change in Vm is very low eventhough we change NMOS 2 to 3 times of PMOS.

  Adavantages:
  +  Vm changes is small with change in NMOS size,which is very important to Inverter behaviour.
  +  I fab makes PMOS size $.5 times of NMOS size,CMOS inverter behaves as it is eventhough there is some vary in required size.
  +  The rise dealy and all delay is samem at same point which is important feature is
    clock cell.
  + If we design CMOS of 1.2V there is possibility to get inverter where there is exactly sam efall and rise delay.
 
  <img width="856" height="506" alt="image" src="https://github.com/user-attachments/assets/85cfab3e-81d0-4777-aab1-4fdf62d2d8b8" />

 + Fou our W/L ratio we may get graph with unequal rise and all time.
 + The above shown picture is image of Clock tree which is made of buffers,where we get both rise time and All time is same.
 + These are known as Clock inverters or clock buffers.
  + PMOS = NMOS where their resistances match.(we didnot see size of PMOS and NMOS,we will take its resistances into or account.)
  + PMOS is 2-2.5 times of NMOS to get equal resistances which is required for clock Inverter.


<img width="707" height="504" alt="image" src="https://github.com/user-attachments/assets/88d6b80a-fe73-4947-aef9-759f67b5281b" />

the above shows about a clock cell where input waveform is equal to output waveform.
+ By using other which is not a clock cell we save area but we get unequal parts of rise eand delay.
+ Depends on end result we select our required Time cells.

    # SETUP analysis

     <img width="821" height="450" alt="image" src="https://github.com/user-attachments/assets/bbeb5b7d-551d-4e9e-8d32-bf55c70cdf5b" />

     Above shows data path and conditions for slack is positiv or zero.
  + for that to be valid we need data arrival time be less tahn data required time.
  + If data required time is less than Data arrival time then we can reduce the daely of data arrival time by plugging required  clock cell to reduce ris edealy as abouve circuit depensds only on RISE delay.

 <img width="784" height="252" alt="image" src="https://github.com/user-attachments/assets/c10dde90-3790-40f6-9a50-9b5931ebc945" />


  + Here we have total of 5 inverters,where we can use one or clock cell and other for delay Time.





# DAY 4.1
# Introduction to Noise margin.
Static behavior Evaluation : CMOS inverter Robustness
2. Noise Margin, NMH and NML

+ What is Noise Margin?
  Noise margin tell about glitchs,cross talk noise in lower node can be identiied before it happens by using NOISE margin.

In real chips there is always some noise present on the wires due to coupling,power supply variation,crosstalk etc.So the inverter must be robust enough to handle this noise.
Noise Margin is a measure of this robustness of the CMOS inverter.

Input and Output of an Inverter

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/60fb4d3a-0148-4174-8168-7c3e2b5c4266" />


From above picture we can observe a simple inverter symbol.
Inverter takes input 0 or 1 and gives output 1 or 0 respectively.
•If input is 0 then output is 1
•If input is 1 then output is 0
This is the basic inversion behaviour.But in real circuits input and output are not ideal 0 or 1.They are voltage levels.So we need to define what voltage range is considered as logic 0 and what range is logic 1.

I/O Characteristic of Inverter
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/2dc14313-431f-434f-a054-70c89d3a42da" />


From above picture we can observe the Ideal I/O Characteristic of a Inverter.
x-axis is Vin and y-axis is Vout.
In ideal case:
+ When Vin is between 0 and Vdd/2: output is Vdd(logic 1)
+ When Vin is between Vdd/2 and Vdd: output is 0(logic 0)
The transition happens exactly at Vdd/2 and it is perfectly vertical.
+ When we increase Vin,at Vdd/2 output voltge Vdd becomes "0".
+ This states that switching happens at Vdd/2.
+ It is behaviour of inverter.When Vin changes from 0 to 1,functioning of NMOS and PMOS changes.

 
Ideal I/O Characteristic with Infinite Slope

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/7cefcba8-14a2-4276-8663-83092277384d" />

From above picture we can observe the Ideal I/O Characteristic with Infinite Slope marked.
Here the transition from Vdd to 0 happens exactly at Vdd/2 with infinite slope where slope is (Change in output voltage/change in input voltage).
+ Infinite slope means the transition is instantaneous - output switches from Vdd to 0 at exactly one point on the input which happens only in ideal condition.


Actual I/O Characteristic with Finite Slope

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/b57e40c1-c896-4a95-84a9-b5232f308642" />

From above picture we can observe both ideal(left) and actual(right) I/O characteristics side by side.
In actual I/O characteristic(right graph):
+ When Vin is low: Vout stays at Vdd(output is HIGH)
+ As Vin increases: Vout starts decreasing.This transition region has a finite slope not infinite slope.This happens due to presense of finite resistance,capacitance in actual circuit.
+ When Vin is high: Vout reaches near to "0" but not exactly "0".
+ The transition is not a perfect vertical line.It is a slanted line with finite slope.This is the ACTUAL behaviour of a real CMOS inverter.
+ The finite slope region is the transition zone where the output is switching from HIGH to LOW.
+ Here we took resistance and capacitance are linear so we got linear shit with a constant slope from high to low.

  
WHY does finite slope matter?
Because the finite slope transition region creates ambiguity.If Vin is in the transition zone the output is neither clearly 0 nor clearly 1.This is the region where noise can cause wrong output.So we need to define clear boundaries for what is logic 0 and logic 1 for both input and output.These boundaries are VIL,VIH,VOL,VOH.

VIL - Input Low Voltage

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/dc5a0e95-feac-4a0e-9aeb-b072fcf361ef" />


<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/48955318-49e4-4444-9a0a-aba733fbe3d9" />



From above picture we can observe VIL marked on the actual I/O characteristic.
VIL is Input Low Voltage
Any input voltage level between 0 and VIL,output is Vdd or high or Voh.
Voh is output high voltage.
+ 



<img width="551" height="307" alt="image" src="https://github.com/user-attachments/assets/4d2534f4-9a0b-4e6e-822c-886ec41ba551" />

VIH is Input High Voltage.

Any input voltage level which lies between VIH and Vdd considered as low or Vol.
Vol is output lowvoltage.


From above picture we can observe VOH marked on the actual I/O characteristic.
VOH is Output High Voltage.


Any output voltage level between VOH and Vdd will be treated as logic 1.
VOH is the minimum output voltage that is recognised as logic 1.
When Vin < VIL: output must be >= VOH.So VOH corresponds to the output when input is in the LOW region.


VOL - Output Low Voltage

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/96031e2c-6929-4f7b-8200-47dad582dc7c" />
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/96031e2c-6929-4f7b-8200-47dad582dc7c" />

From above picture we can observe VOL marked on the actual I/O characteristic.
VOL is Output Low Voltage
Any output voltage level between 0 and VOL will be treated as logic 0.
VOL is the maximum output voltage that is still recognised as logic 0.
When Vin > VIH: output must be <= VOL.So VOL corresponds to the output when input is in the HIGH region.

All 4 Parameters Together
From above pictures we can observe all 4 parameters on the actual I/O characteristic.
Summary of all 4 parameters:
•VIL = Input Low Voltage.Max input voltage treated as logic 0.
•VIH = Input High Voltage.Min input voltage treated as logic 1.
•VOH = Output High Voltage.Min output voltage treated as logic 1.
•VOL = Output Low Voltage.Max output voltage treated as logic 0.

Forbidden zones:
•Input forbidden zone: voltage between VIL and VIH.Should not operate here.
•Output forbidden zone: voltage between VOL and VOH.Output should never be in this range.

Noise Margin - NMH and NML
Now we can define Noise Margin using these 4 parameters.

NMH = Noise Margin High
NMH = VOH - VIH
NMH tells us how much noise can be tolerated on a HIGH signal.
If output of gate A is VOH and input of gate B needs VIH then the diference(VOH - VIH) is the margin available before noise corrupts the HIGH signal.
Larger NMH means more robust circuit in HIGH state.

NML = Noise Margin Low
NML = VIL - VOL
NML tells us how much noise can be tolerated on a LOW signal.
If output of gate A is VOL and input of gate B must be below VIL then the diference(VIL - VOL) is the margin available before noise corrupts the LOW signal.
Larger NML means more robust circuit in LOW state.

WHY Noise Margin is important?
In a real chip there are millions of gates connected together.The output of one gate feeds into input of next gate.
Due to noise on wires,the voltage level can shift.If the noise is larger than the noise margin then the receiving gate will misinterpret the signal and give wrong output.
So we want:
•NMH to be as large as possible so HIGH signals are not misinterpreted
•NML to be as large as possible so LOW signals are not misinterpreted
For a symmetric inverter(with equal PMOS and NMOS strength):
•VIL is slightly above 0
•VIH is slightly below Vdd
•VOH is close to Vdd
•VOL is close to 0
So both NMH and NML are large.This is one reason CMOS is preferred over other logic families.


.............................................................
# 4.2


Why We Need Noise Margin Parameters
In a real inverter, the VTC is not a perfect rectangle. The output does not switch instantly from Vdd to 0. Because of this finite slope, we cannot simply say 'anything above Vdd/2 is logic 1 and anything below is logic 0'. We need a more careful set of definitions.

Noise margin voltage parameters are those definitions. They tell us exactly what voltage ranges count as valid logic 0 and valid logic 1  both at the input and the output. They also tell us how much noise the circuit can tolerate before it misreads a signal.

1. Ideal vs Actual Inverter VTC

 <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/7e8387aa-fea0-4fc0-a362-6c895faf5ad1" />

Ideal Inverter VTC — Infinite Slope
In an ideal inverter:
•Vout = Vdd for all Vin < Vdd/2
•Vout switches instantly to 0 at Vin = Vdd/2
•Vout = 0 for all Vin > Vdd/2

This gives a perfectly rectangular VTC with infinite slope at the switching point. No ambiguity — any input either produces exactly Vdd or exactly 0.

Actual Inverter VTC — Finite Slope
In a real CMOS inverter the VTC has a finite slope. This means:
•Vout starts near Vdd (but not exactly Vdd) for low Vin
•Vout falls gradually through a transition region around Vdd/2
•Vout settles near 0 (but not exactly 0) for high Vin


2. VOL — Output Low Voltage
Definition
VOL  =  Maximum Vout when output is logic 0

'VOL is Output Low Voltage'
 Any output voltage level between 0 and VOL will be treated as logic 0'

So if the output of a gate is anywhere between 0 V and VOL, the receiving gate will correctly interpret it as logic 0.

By Observation from the VTC
When Vin is HIGH (near Vdd), the NMOS is strongly ON and PMOS is OFF. NMOS pulls Vout toward Vss = 0. But because NMOS has a finite ON resistance Rn, Vout does not reach exactly 0. It settles at a small positive value — this is VOL.

VOL > 0 always in a real gate. The magnitude of VOL depends on the NMOS W/L ratio. A wider NMOS (smaller Rn) gives a smaller VOL, which is better.

3. VOH — Output High Voltage

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/3bbc5ef0-058d-4514-9176-fbc186489627" />

 The above graph shows nearly actual situation.The slope in mid range is still negative.

 Case 1:
 + If input value lies in 0,VIL then it is considered as
   + logic 0 for input
   + Nearly logic 1 for Output.we call it nearly beacause graph is not showing ideal nature and has some deviation due to resistance,capacitance and other parameters.

Case 2:
+  If input value lies in VIH and Vdd
 + The input voltage logic is 1
 + Output voltage logic is Zero.

HERE WE EXPALINED ABOVE POINTS CLEARLY
 


VIL — Input Low Voltage

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/fb6ab90d-a52b-431a-8475-2467f4cf5a04" />

Definition
VIL  =  Maximum Vin that is treated as logic 0

Any Vin between 0 and VIL is guaranteed to produce a valid HIGH output (Vout >= VOH). The gate treats it as a reliable logic 0 input.

How to find VIL on the VTC
VIL is found at the point on the upper part of the VTC where the slope equals -1.

Slope = -1 means:  dVout/dVin = -1  at that point

This is the unity-gain point on the upper slope. At this point, a 1 V increase in Vin causes exactly a 1 V decrease in Vout. Below VIL, the gain is less than 1 (Vout is relatively stable). Above VIL, the gain becomes greater than 1 and the output starts falling rapidly.

So VIL is the boundary between the reliable LOW input region and the start of the transition zone.

5. VIH — Input High Voltage

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/b1fef2c0-df73-4e8a-a5fb-c2c7a3d68edc" />

Definition
VIH  =  Minimum Vin that is treated as logic 1

Any Vin between VIH and Vdd is guaranteed to produce a valid LOW output (Vout <= VOL). The gate treats it as a reliable logic 1 input.

<img width="791" height="413" alt="image" src="https://github.com/user-attachments/assets/27aa89ec-e180-4b2a-813b-d257453518ae" />


How to find VIH on the VTC
VIH is found at the point on the lower part of the VTC where the slope also equals -1.

Slope = -1 means:  dVout/dVin = -1  at that point

This is the unity-gain point on the lower slope. Above VIH, the gain is less than 1 and Vout is stable in the LOW region. Below VIH (but above VIL), the gain is greater than 1 and the output is in the transition zone.

Input Voltage Ranges Summary
•Valid logic 0 input:  0  <=  Vin  <=  VIL  =>  output is guaranteed HIGH
•Undefined input:  VIL  <  Vin  <  VIH  =>  output is unpredictable (forbidden zone)
•Valid logic 1 input:  VIH  <=  Vin  <=  Vdd  =>  output is guaranteed LOW


  Finding VIL and VIH — The Slope = -1 Method

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/0442dc5b-097b-4af0-bfca-7ae1d73bdab3" />

Both VIL and VIH are found by drawing a tangent line with slope = -1 on the actual VTC.

•Upper slope = -1 point:  on the high Vout region of the VTC  =>  this is VIL
•Lower slope = -1 point:  on the low Vout region of the VTC   =>  this is VIH

WHY slope = -1?

The slope of the VTC is dVout/dVin — the voltage gain of the inverter. When gain = -1 (slope = -1), the circuit is at the boundary between stable and unstable operation. Below gain = -1 in magnitude (|gain| < 1), the output changes less than the input — the gate is in a stable region. Above gain = -1 in magnitude (|gain| > 1), the output changes more than the input — the gate is in the high-gain transition region where logic levels are unreliable.

So slope = -1 is the exact boundary that separates valid input ranges from the undefined transition zone. This is why VIL and VIH are defined there.


Summary — Key Points from This Lecture
•Real inverters have a finite-slope VTC — not the ideal infinite-slope rectangle.
•VOL = max output for logic 0. VOH = min output for logic 1.
•VIL = max input treated as logic 0. VIH = min input treated as logic 1.
•VIL and VIH are found at the slope = -1 (unity gain) points on the actual VTC.
•NML = VIL - VOL   (noise margin for LOW signals)
•NMH = VOH - VIH  (noise margin for HIGH signals)
•Larger noise margins = more robust digital circuit.
•SPICE simulations from earlier lectures are used to extract these 4 parameters from the actual VTC.



.............................................................................

# 4.3

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/4453698e-5588-48cd-a1a3-0b0f284b7dd7" />
 We plot all voltage levels attained on the graph,on scale.
 + Here we are tryong to NOise margin.
 + It defines input voltage range and output voltage range.
 + we discussed Voh > Vin.so it decides logic 1 to next stage of input.
 + Any voltage which is higher than Vih is denoted as logic 1.
 + so,for next stage to consider it as high/1,Voh should be greater than Vih and near to Vdd.
 + Next highe rvalue is Vih.
 + There is area which is undefined.The next voltage is Vil.
 + If output is connected to next logic then when we consider output shold be minimum only when Vol is less than Vil.
 + lowest voltage present output should be less than Vil.
 + So lowest is Vol.

<img width="113" height="237" alt="image" src="https://github.com/user-attachments/assets/a0545182-088b-438d-a0de-7da340b0de29" />

From all of our assummptions we get above plot.
1. Any voltage level which lies in Voh and Vih,It is known as NOISE margin high as it gves logic 1 at both input and output sides.
   Vin = [Vih,Voh] is known as NM <sub> h </sub>.
2. Any voltage level which lies in range of Vol and Vil in any side output or input side,It is denoted as Logic "0".It is know as NOISE  MARGIN low(NMl)
   Vin=[Vol,Vil] is known as Noise margin LOW.(NMl)    


NOISE MARGIN HIGH = Voh -Vih
NOISE MARGIN LOW  = Vil - Vol

If bumps lies in Noise Margin High region or Noise Margin low region,it is tolerable.The noise generated in thes emargins is easily removable without harming any circuit.
+ th other parameters that decides noise is Noise split.
+ The region between Vih and Vil is undefined region.
+ ANy bump lies in this region goes into undefined state where it can be logic 0 or logic 1.

WHY is the Undefined Region dangerous?
When the input is in the undefined region, both PMOS and NMOS are partially conducting. The gate is in its high-gain transition region. A tiny change in input produces a large change in output. The output can land anywhere between VOL and VOH — not at a reliable logic level.

If one gate in a logic chain produces an output in the undefined region, the next gate also receives an input in an unpredictable range. Errors can cascade through the entire circuit. This is why the transition through the undefined region must happen as quickly as possible during switching.


5. Noise Margin Summary — Three Cases of Noise Bumps

   <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/4be40362-06a2-4ca1-a5aa-a52095f2599b" />


heights relative to the NML, Undefined Region, and NMH bands (~3:30)
From the slide title: 'Noise Margin Summary'
From the slide caption: 'Noise induced bump characteristics at different noise margin levels'
From the slide text: 'For any signal to be considered as logic 0 and logic 1, it should be in the NML and NMH ranges, respectively.'

The diagram shows a signal at a LOW voltage level (near VOL) with three different noise bumps of increasing height:

Case a) — Small noise bump (bump < NML)
From the slide:  'Bump height lies between Vol and Vil. Will be considered as logic 0'

•Signal baseline is at or near VOL
•Noise bump rises above VOL but stays below VIL
•Entire bumped signal stays within the NML zone (0 to VIL)
•Receiving gate reads it correctly as logic 0
•Circuit works correctly — noise margin successfully absorbed the bump

Case b) — Medium noise bump (bump enters Undefined Region)
From the slide:  'Bump height lies between Vil and Vih. Output logic undefined'

•Signal baseline is at VOL
•Noise bump rises above VIL and into the undefined region (between VIL and VIH)
•The signal is now in the uncertain zone
•Receiving gate output is unpredictable — may be anywhere between VOL and VOH
•This is a marginal case — circuit may or may not work. Not acceptable in reliable design.

Case c) — Large noise bump (bump > NML + Undefined Region, enters logic 1 zone)
From the slide:  'Bump height lies between Vih and Voh. Will be considered as logic 1'

•Signal baseline is at VOL (intended logic 0)
•Noise bump rises above VIH, entering the logic 1 zone
•Receiving gate reads it as logic 1 — this is a full logic error
•Circuit fails — what was supposed to be 0 has been corrupted to 1 by noise

6. Summary — Key Points from This Lecture
The two noise margin equations
NMH  =  VOH  -  VIH
NML  =  VIL  -  VOL

Three voltage regions on the input voltage axis
•0 to VIL          → Valid logic 0 input zone. Gate output is guaranteed HIGH.
•VIL to VIH        → Undefined Region. Gate output is unpredictable. Avoid this.
•VIH to Vdd         → Valid logic 1 input zone. Gate output is guaranteed LOW.

What noise margins tell us
•NML = how much noise a LOW signal can absorb before it is misread
•NMH = how much noise a HIGH signal can absorb before it is misread
•Larger NML and NMH = more robust circuit
•CMOS has large noise margins because VOL ≈ 0 and VOH ≈ Vdd

Three noise bump cases — what determines circuit behaviour
•Bump < NML (or < NMH): stays in valid zone → circuit works correctly
•Bump enters Undefined Region: unpredictable output → marginal and unreliable







............................................................................
# 4.4

Noise margin variation with respect to PMOS width
Static behavior Evaluation : CMOS inverter Robustness
2. Noise Margin, NMH and NML

Setup

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/9cfed354-0347-4944-a57f-802e6284e1be" />

The purpose of this experiment is how Noise Mrgon changes with change in size of NMOS with respect to PMOS.

From above picture we can observe the experiment setup.
table on the left side with two columns:
•Wp/Lp: PMOS width to length ratio (kept same Wp/Lp in all cases)
•x.Wn/Ln: NMOS width multiplied by x (this is the PMOS width relative to NMOS)

We run 5 SPICE simulations.In each simulation we increase the PMOS width:
•Row 1: Wp/Lp with Wn/Ln  (PMOS width = 1x NMOS width)
•Row 2: Wp/Lp with 2Wn/Ln (PMOS width = 2x NMOS width)
•Row 3: Wp/Lp with 3Wn/Ln (PMOS width = 3x NMOS width)
•Row 4: Wp/Lp with 4Wn/Ln (PMOS width = 4x NMOS width)
•Row 5: Wp/Lp with 5Wn/Ln (PMOS width = 5x NMOS width)



Case 1: Wp/Lp with Wn/Ln (1x PMOS width)
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/237645a3-a3b5-4ca1-a108-0ffe8427956e" />

From above picture we can observe Case 1 with PMOS width = 1x NMOS width.
This is the baseline case where PMOS and NMOS have same width.
We can observe:
•Vm = 0.99v (switching point is below Vdd/2 = 1.25v)
•VTC curve transitions around Vin = 1v
•NMH = 0.3
•NML = 0.3

WHY is Vm below Vdd/2?
Because PMOS is naturally weaker than NMOS for same width(PMOS mobility is lower than NMOS mobility).So NMOS wins the fight earlier and pulls output LOW at a lower Vin.To make Vm = Vdd/2 we need to make PMOS stronger by increasing its width.

Case 2: Wp/Lp with 2Wn/Ln (2x PMOS width)
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/debd5b9a-f3c3-4d60-afb3-2797c21082d8" />

From above picture we can observe Case 2 with PMOS width = 2x NMOS width.
We can observe:
•Vm = 1.2v (switching point shifted right compared to Case 1)
•VTC curve shifted to the right.PMOS is now stronger so it holds output HIGH for longer.
•NMH = 0.35 (increased from 0.3)
•NML = 0.3 (same as Case 1)

From above picture we can observe that increasing PMOS width shifts the VTC curve to the right.This means the inverter switches at a higher Vin.NMH increases because VOH stays at Vdd but VIH moves to the right.

Case 3: Wp/Lp with 3Wn/Ln (3x PMOS width)

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/59b1a21c-6136-4620-ab61-3ba0269e7c23" />

From above picture we can observe Case 3 with PMOS width = 3x NMOS width.
We can observe:
•Vm = 1.25v (switching point is now exactly at Vdd/2 = 1.25v)
•VTC curve is now symmetric.This is the balanced inverter condition.
•NMH = 0.4 (further increased)
•NML = 0.3 (still same)

From above picture we can observe that at 3x PMOS width the inverter is symmetric.Vm = Vdd/2 = 1.25v.This is because PMOS mobility is roughly 2-3x lower than NMOS mobility so we need 2-3x wider PMOS to balance.

Case 4: Wp/Lp with 4Wn/Ln (4x PMOS width)
<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/130ed808-8d8f-4084-9f46-113fe32795db" />

From above picture we can observe Case 4 with PMOS width = 4x NMOS width.
We can observe:
•Vm = 1.35v (switching point shifted further right)
•VTC curve shifted even more to the right.PMOS is now stronger than NMOS.
•NMH = 0.42 (increased further)
•NML = 0.27 (decreased from 0.3)

Here we can observe that NMH is increasing but NML is now decreasing.This is because when PMOS is too strong the output LOW level(VOL) starts rising slightly and VIL shifts left.So NML = VIL - VOL becomes smaller.

Case 5: Wp/Lp with 5Wn/Ln (5x PMOS width)

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/c08e6214-665c-4970-aea4-6f06a34cd66b" />

From above picture we can observe Case 5 with PMOS width = 5x NMOS width.
We can observe:
•Vm = 1.4v (switching point shifted even further right)
•VTC curve continues to shift right.
•NMH = 0.42 (same as Case 4, no further improvement)
•NML = 0.27 (same as Case 4, no improvement)

From above picture we can observe that beyond 4x PMOS width there is no further improvement in NMH.Both NMH and NML have saturated.Increasing PMOS width further just keeps shifting Vm to the right but does not help noise margin anymore.

Complete Results Table

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/0e7631fd-6666-49c0-9b24-c2d9a595d9b1" />


Table summary:
•Wp/Lp with Wn/Ln:   NMH = 0.3,  NML = 0.3,  Vm = 0.99v
•Wp/Lp with 2Wn/Ln:  NMH = 0.35, NML = 0.3,  Vm = 1.2v
•Wp/Lp with 3Wn/Ln:  NMH = 0.4,  NML = 0.3,  Vm = 1.25v
•Wp/Lp with 4Wn/Ln:  NMH = 0.42, NML = 0.27, Vm = 1.35v
•Wp/Lp with 5Wn/Ln:  NMH = 0.42, NML = 0.27, Vm = 1.4v

Key observations from table:
•As PMOS width increases: Vm increases(VTC shifts right)
•NMH increases as PMOS width increases upto 4x then saturates
•NML stays same upto 3x then decreases after 4x
•Best balanced noise margin is at 3x PMOS width where Vm = Vdd/2 and both NMH and NML are reasonable

Connection to Digital Design

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/e5233755-9b8e-4e36-801f-2401eb9e9faa" />


<img width="790" height="443" alt="image" src="https://github.com/user-attachments/assets/d684fa79-52bf-455f-9f2f-84cc192c725e" />


From above picture we can observe the connection to Digital Design concept marked on the VTC.
+ For digital design,the values are taken in NOise margin regions.
+ For analog design the values between these margins or in undeined region is used.
+ 
In Digital Design we always assume inverter is symmetric and VTC is ideal.But in real CMOS design:
•PMOS is always made 2x to 3x wider than NMOS to compensate for lower PMOS mobility.
•This ensures Vm is close to Vdd/2 which gives symmetric NMH and NML.
•If we dont size PMOS correctly then Vm shifts and one of NMH or NML becomes too small.
•Small noise margin means the circuit can give wrong output even with small noise on the wire.




..........................................................................

#LECTURE 40

............................................................................

#LECTURE 41

What is this lecture about?
In previous lectures we changed PMOS width and saw how VTC and noise margin changes.
Now in this lecture we want to see what happens when Vdd changes.What if someone gives 2.5V chip only 1V supply?Will it still work?
So the question is - how does VTC change when Vdd is scaled down from 2.5V to 1V?
To answer this we run multiple SPICE simulations - one for each Vdd value.But doing this manually for every Vdd is boring and slow.So in this lecture we learn a SMART way to run all simulations automatically using a loop inside the SPICE netlist itself.

Circuit Setup
<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/c1276d21-f1bd-4057-9228-5b31efe57157" />


From above picture we can observe the inverter circuit used for this experiment.
Circuit parameters are:
•Vdd = 2.5V (starting value, will be scaled down)
•Wp = 0.9375u (PMOS width)
•Wn = 0.375u (NMOS width)
Note: Wp is 2.5x Wn.This is the balanced sizing we learned in previous lecture to get Vm near Vdd/2.

The Experiment - What are we doing?

<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/f84a790b-f8cb-462f-b05d-276467127fef" />

From above picture we can observe the plan.
Same inverter.Same transistor sizes.Only one thing changes - Vdd.
We want to run VTC simulation 5 times:
•Run 1: Vdd = 2.5V
•Run 2: Vdd = 2.0V
•Run 3: Vdd = 1.5V
•Run 4: Vdd = 1.0V
•Run 5: Vdd = 0.5V

Each run gives one VTC curve.At the end we get 5 curves on the same plot.We can see how VTC shape changes as Vdd goes down.

We could write 5 separate netlist files.But that is silly and slow.Instead we write ONE netlist with a loop that does all 5 runs automatically.This is the "smart" part.

Reference VTC at Vdd = 2.5V

<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/78075046-4a7a-44df-a2ef-fb079b87b8fb" />


From above picture we can observe the VTC curve at Vdd = 2.5V with region labels.
This is the reference VTC we already know from previous lectures.
5 regions are visible on the curve:
•PMOS linear, NMOS off - at very low Vin,output = Vdd
•PMOS linear, NMOS sat - Vin just above Vtn,NMOS starts conducting
•PMOS sat, NMOS sat - both in saturation,sharp transition region
•PMOS sat, NMOS linear - Vin high,NMOS pulls output low
•PMOS off, NMOS linear - at very high Vin,output = 0
This is the full VTC at 2.5V.Now we want to see what happens at lower Vdd values.

The Smart SPICE Netlist - How the loop works
Instead of writing 5 separate netlists,the instructor writes ONE netlist with a loop.This is the clever part of this lecture.

<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/07ae54dd-3382-4c15-a942-926bf569c959" />

From above picture we can observe the top part of the SPICE netlist file called ScalingSupplyVoltageExp.
The netlist starts with standard MODEL and component descriptions:
*** MODEL Descriptions ***
*** NETLIST Description ***
***2.5 supply voltage***
M1 out in vdd vdd pmos W=0.9375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u
cload out 0 10f
Vdd vdd 0 2.5
Vin in 0 2.5

M1 is PMOS with Wp=0.9375u.M2 is NMOS with Wn=0.375u.cload is 10fF load cap.Vdd starts at 2.5V.Vin sweeps from 0 to 2.5V to get VTC.

<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/9882b8e3-f88f-4efa-89c7-f0523c7bef69" />


From above picture we can observe the .control section which is the "smart" loop part.
The .control block is a special ngspice section where you can write control commands like a simple program.

The loop works like this:
.control
let powerSupply = 2.5
alter Vdd = powerSupply

    let voltageSupplyVariation = 0
    dowhile voltageSupplyVariation < 5
        dc Vin 0 2.5 0.01
        let powerSupply = powerSupply - 0.5
        alter Vdd = powerSupply
        let voltageSupplyVariation = voltageSupplyVariation + 1
    end

    plot dc1.out vs in dc2.out vs in dc3.out vs in dc4.out vs in dc5.out vs in
    xlabel "input voltage [V]" ylabel "output voltage [V]"
    title "Inverter dc characteristics as a function of supply voltage"
.endc

Let us understand each part of the loop step by step:

<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/6d7ecfd2-7c1a-41d0-b367-b097aa262a3b" />

From above picture we can observe the dc Vin 0 2.5 0.01 line is highlighted.This is the DC sweep command inside the loop.

Step by step loop explanation:
•let powerSupply = 2.5 : creates a variable called powerSupply and sets it to 2.5V
•alter Vdd = powerSupply : tells SPICE to change Vdd to whatever powerSupply is
•let voltageSupplyVariation = 0 : this is the loop counter.starts at 0.
•dowhile voltageSupplyVariation < 5 : keep looping as long as counter is less than 5.So loop runs 5 times.
•dc Vin 0 2.5 0.01 : sweep Vin from 0 to 2.5V in steps of 0.01V.This gives one VTC curve.
•let powerSupply = powerSupply - 0.5 : reduce Vdd by 0.5V for next iteration
•alter Vdd = powerSupply : apply the new Vdd
•let voltageSupplyVariation = voltageSupplyVariation + 1 : increment counter
•end : go back to dowhile check

So the 5 iterations run at Vdd = 2.5, 2.0, 1.5, 1.0, 0.5V one by one automatically.No manual work needed.

<img width="700" height="310" alt="image" src="https://github.com/user-attachments/assets/ddbb11d7-aef8-49c7-b5f6-96b26eec2d90" />

From above picture we can observe the entire .control block highlighted showing the full loop structure.
After the loop finishes,the plot command puts all 5 VTC curves (dc1.out through dc5.out) on the same graph.


#SIMULATION RESULTS

From above picture we can observe the final result more clearly.
We can observe very clearly how the VTC changes as Vdd is scaled down:
•dc1 out (Vdd = 2.5V): largest curve.Output goes from 2.5V down to 0V.Transition happens around Vin = 1.25V.
•dc2 out (Vdd = 2.0V): slightly smaller.Output swings from 2.0V to 0.
•dc3 out (Vdd = 1.5V): curve gets narrower.Output swings from 1.5V to 0.
•dc4 out (Vdd = 1.0V): small curve.Transition getting less sharp.
•dc5 out (Vdd = 0.5V): tiniest curve at bottom.Output swing is very small.VTC is barely visible.

The most important observation is - as Vdd decreases the VTC curve shrinks and the transition gets less sharp.At very low Vdd the curve becomes very soft which means noise margin gets very small.

WHY this matters?
1. Modern chips run at low Vdd:
Chips in 2024 run at 0.7V to 1.0V.Not 2.5V.This is done to save power.Power = C * Vdd^2 * f.Lower Vdd means much less power.So this experiment directly shows what happens to VTC and noise margin in modern low power chips.

2. Noise margin shrinks at low Vdd:
Look at dc5 curve at 0.5V.The VTC is barely distinguishable.NMH and NML are tiny.This means the circuit is very sensitive to noise.In real chips at very low Vdd,careful noise and variation analysis is needed.

3. Why use a loop instead of 5 separate netlists?
Using .control loop is a professional SPICE technique.In real industry you will run hundreds of corners and conditions.Writing separate netlist for each is not practical.The loop approach is scalable.Change one number and you can run 10 or 100 iterations.This is the smart way to simulate.

4. The alter command:
alter Vdd = powerSupply is a powerful command.It lets you change a component value mid-simulation without rewriting the netlist.In real chip verification teams use this to sweep process corners,temperature,and voltage systematically.


......................................................................

# LECTURE42

 what happens when we scale Vdd down? Like really bring it down, all the way to 0.5 V.

This is called Power Supply Scaling. We run 5 separate SPICE DC simulations:

•dc1  →  Vdd = 2.5 V
•dc2  →  Vdd = 2.0 V
•dc3  →  Vdd = 1.5 V
•dc4  →  Vdd = 1.0 V
•dc5  →  Vdd = 0.5 V

All 5 VTCs are plotted on the same graph. Then we check gain and energy at each Vdd.
Spoiler: lower Vdd gives you better gain AND way less energy. But it also makes the inverter horribly slow.

1.  The 5-VTC Overlay — What It Looks Like

2.  <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/bc834466-2fbe-4709-8cf7-816e362e97e3" />

ach VTC is a different curve on the same axes.

By Observation:
•As Vdd goes down, the whole VTC shifts left and compresses.
•The switching threshold Vm (middle of the transition) also scales down with Vdd.
•The curve at 0.5 V (dc5) is squeezed into a tiny input range — it looks very steep.
•At 2.5 V (dc1), the VTC is wide and gradual. The transition happens over a larger Vin range.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/02d98844-1621-4f07-9060-b7b5ea9e3673" />

2.  Gain — What Changes When Vdd Goes Down?
Gain = slope of the VTC at the steepest point = dVout/dVin in the transition region.
The steeper the transition, the higher the gain.

Gain at Vdd = 2.5 V  (dc1)
|gain| = 7.38   at Vdd = 2.5 V

Gain at Vdd = 0.5 V  (dc5)

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/4b7dd298-4d19-4f2f-b1cf-0551f3eb877c" />

Improvement:  11.53 / 7.38 ≈ 1.56  →  56% increase in gain

WHY does gain increase when Vdd drops?
Think about what gain means physically.

•The transistor threshold voltages Vtn and Vtp do NOT scale — they are fixed by the sky130 process.
•But the supply voltage is smaller, so the output swing is smaller too.
•The VTC still has to switch from Vout = Vdd to Vout = 0 in roughly the same Vin window near Vth.
•But now Vdd is much smaller, so the transition is compressed into a shorter vertical drop.
•Shorter vertical drop over the same horizontal Vin range = steeper slope = higher gain.

The transistors squeeze the full logic swing into a tighter space. Gain goes up.

3.  Energy — The Huge Win at Low Vdd
The Energy Equation

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/5d41c6db-89b0-477d-ab58-1aa8b90f24b7" />

Energy  =  ½ C V²

•C:  load capacitance at output (fixed by the circuit, doesn't change with Vdd)
•V:  the supply voltage Vdd

Energy scales with V SQUARED. This is the key insight.
Cut V in half → energy drops to ONE QUARTER. Not half. One quarter.

Energy at Vdd = 0.5 V


At Vdd = 0.5 V:
Energy  =  ½ C (0.5)²  =  ½ C × 0.25

At Vdd = 2.5 V:
Energy  =  ½ C (2.5)²  =  ½ C × 6.25

Ratio:  0.25 / 6.25 = 0.04  →  energy at 0.5V is only 4% of what it was at 2.5V
That is a 96% reduction in switching energy.

WHY does energy drop so fast?
Because E = ½CV² has V squared in it.

•V is not linear — the relationship is quadratic.
•Every time you halve V, energy drops by a factor of 4.
•This quadratic behaviour is exactly why chip designers obsess over reducing Vdd.
•Modern chips run at 0.7–1.0 V instead of the old 5V days. This is the reason.


Advantages of using 0.5 V supply:
 •Increase in gain  →  close to 50% improvement  (we measured ~56%)
 •Significant reduction in energy  →  close to 90% improvement.

 5.  The Big Problem — Delay Goes Through the Roof
OK. So we get more gain and way less energy. Sounds perfect right?
Why don't we just run everything at 0.5 V?

Because there is one huge problem: the inverter becomes very slow.

Dynamic Simulation at 0.5 V

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/06f5ab57-4784-4e30-bafe-fce5c3d27756" />


By Observation:
•The y-axis is in mV, not V. The output swing is tiny.
•Rise and fall transitions are sluggish and drawn out over many nanoseconds.
•The inverter can barely switch. The output looks smeared and weak.
•This is the disadvantage — very high propagation delay.

Dynamic Simulation at 2.5 V — for Comparison

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/4f7f12e0-ef97-4cee-9399-7530a369327e" />

By Observation:
•Output is a crisp inverted square wave.
•Transitions happen very fast — almost vertical edges.
•The inverter works exactly as expected at full supply voltage.

The difference between 0.5 V and 2.5 V dynamic behaviour is night and day.

WHY is delay so bad at low Vdd?
Two things cause this:

•1. Less overdrive voltage:
+Overdrive = Vgs − Vt
+At Vdd = 0.5V and Vt ≈ 0.4V (sky130 NMOS), overdrive is only 0.1V when input is HIGH.
+Almost no overdrive = transistor barely turns on = very high ON resistance Rn.

•2. High Rn × CL = high delay:
+Delay to charge/discharge CL is proportional to Ron × CL.
+We already know: Ron is huge at 0.5V.
+Big resistance × fixed capacitance = slow RC charging = slow switching.

There is no way to fix this without changing the process or topology. It is a fundamental trade-off.

6.  Summary — The Power-Delay Trade-Off
Lower Vdd → better gain, much less energy, but slower speed.
Higher Vdd → worse gain, more energy, but faster speed.
This is called the Power-Delay Trade-Off. Every chip designer has to choose where to sit on this curve.

•Vdd = 0.5 V  →  |gain| = 11.53, energy ≈ 4% of 2.5V case, delay = very high
•Vdd = 2.5 V  →  |gain| = 7.38, energy = 100% (baseline), delay = very low

Real-world applications:
•IoT sensor, wearable, pacemaker  →  run at low Vdd, accept slow speed, save battery
•CPU, GPU, high-speed comms  →  run at higher Vdd, accept higher power, get fast computation

...................................................................

# lECTURE43


....................................................................

# LECTURE 44

PART 1 — Sources of Variation: Etching Process Variation
—WHERE does variation actually come from?

A: It comes from the fabrication process itself.

Two big sources get covered in this lecture:

•Etching process variation  →  affects the physical shape of the transistor gate
•Oxide thickness variation  →  affects the gate oxide, which changes Cox and Vt



1.  What Does an Inverter Actually Look Like on Silicon?

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/6060bfd7-83a0-4dc2-ba89-c42ef8fec72c" />
Before we can talk about variation, we need to understand what's actually being fabricated.

A single CMOS inverter has 2 transistors — 1 PMOS and 1 NMOS.
In layout, these are made from three layers stacked and patterned:

•Poly (Red):  this is the gate. It's a polysilicon strip crossing over the active region.
•P Diff / N Diff (Green):  the diffusion regions. These become source and drain.
•Metal (Blue):  the wires connecting Vdd, Vss, In, Out.

The PMOS transistor sits at the top (connected to Vdd). The NMOS sits at the bottom (connected to Vss).
Both gates are tied together — that's the input In (blue wire through the middle).

By Observation:
•The Poly strip runs vertically (red bar) and crosses through both P Diff and N Diff.
•Where Poly crosses Diff = that's the transistor channel. That's where switching happens.
•The key dimensions are L (length of the gate = width of the red Poly strip) and W (width of the channel = length of green Diff region).

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/2ecf167d-5296-4f69-bbd3-279258fd681d" />

L is THE most important dimension in chip design.
When people say '5nm process' or '28nm node' — they are talking about L. That's the gate length.

L and W together set the transistor's drive strength, speed, and leakage.

2.  Scaling Up — The Inverter Chain

   <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/8afb04ff-464d-4082-995e-9b913ce91b3b" />

   side by side, each showing Poly (red), P Diff and N Diff (green), Metal (blue). (~2:00)
A single inverter is easy to visualise. But real chips have millions of gates chained together.
So now we look at a chain of 8 inverters in series.

In the layout view, you can see 8 identical inverter cells sitting next to each other in a row.
Every cell has:

•Its own Poly gate (red strip)
•Its own P Diff (top green) and N Diff (bottom green)
•Shared Vdd rail at the top (blue horizontal bar)
•Shared Vss rail at the bottom (blue horizontal bar)

The output of each inverter feeds directly into the gate (Poly) of the next one.

By Observation:
•All 8 inverters look identical in the layout — same L, same W, same structure.
•The middle inverters in the chain are sandwiched between two identical neighbours on both sides.
•This matters — because a gate's electrical environment (what's connected to it) affects its behaviour.

3.  The Problem — Ideal Mask vs Actual Mask

   <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/29132c8a-8ffa-4a1c-a3d0-809cee13015c" />

   When a chip is designed, the designer draws a perfect rectangle for the Poly gate.
Clean edges. Exact L. Exact W. That's the Ideal Mask.

But when the chip is actually fabricated — something happens.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/8ae92b9e-2d61-4474-801c-8136096ec4a6" />

Look at that jagged edge on the Actual Mask.

That roughness is caused by the etching process — and it's unavoidable.

WHY does etching cause this?
To pattern the Poly gate on silicon, you use photolithography + chemical etching:

•You shine UV light through a photo mask to expose a pattern on the wafer.
•Then chemicals etch away the exposed Poly, leaving the gate behind.
•But the chemical etch is not perfectly uniform across the whole wafer.
•Light diffraction causes edges to be blurry at nanometre scales.
•The result — the Poly edge ends up rough and jagged instead of clean.

This means the actual L (gate length) on the silicon is NOT exactly what the designer drew.
It varies slightly from transistor to transistor, across the chip, and across wafers.

4.  Why Middle Gates Are Different from Edge Gates
5.  <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/9f3323b1-5664-4ffb-a2ca-9285b20d8be9" />

Now here's something subtle but important.

The middle gates in the chain have the same layout structure on both left and right.
Gate 3 has Gate 2 on its left and Gate 4 on its right. Both are identical.
This means the etch chemistry around Gate 3 is symmetric — it sees the same environment from both sides.

But the first gate and the last gate are at the edge of the chain.
Gate 1 has open space on its left and Gate 2 on its right — asymmetric environment.

By Observation:
•Middle gates: symmetric neighbourhood → etch variation tends to cancel out → L is closer to designed value.
•Edge gates: asymmetric neighbourhood → etch behaves differently on each side → L can shift more.
•This is called 'edge effect' or 'proximity effect' in lithography.

WHY does neighbourhood matter for etching?
•The etching chemicals are shared across the surface of the wafer.
•Dense regions (many Poly features nearby) etch differently than sparse regions (open space nearby).
•A gate at the edge sees more open space on one side → etch loading effect → slightly different L.
•This is a real concern for yield — edge gates behave slightly differently from middle gates even on the same chip.

5.  How Etching Variation Hits the Circuit

   <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/765c1082-1c76-4f27-965f-5f714987ab3a" />

   The drain current equation for a MOSFET in triode (linear) region:

Id  =  u Cox (W/L) [(Vgs − Vt)Vds − Vds²/2]

Let's look at what each term means:

•u (mu):  carrier mobility — electrons for NMOS, holes for PMOS. Fixed by process.
•Cox:  gate oxide capacitance per unit area = epsilon_ox / t_ox. Fixed by process.
•W/L:  the width-to-length ratio of the transistor. Set by the designer — but affected by etch!
•(Vgs − Vt)Vds − Vds²/2:  the voltage-dependent part. Set by circuit operating conditions.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/a47494ab-7002-4901-a9e5-937039797d6d" />

There it is. The orange arrow connecting the ragged Actual Mask to the (W/L) term.

By Observation:
•Etching variation changes the actual L on silicon.
•If L increases slightly → W/L decreases → Id decreases → transistor is weaker → slower gate.
•If L decreases slightly → W/L increases → Id increases → transistor is stronger → faster gate (but also higher leakage).

WHY is W/L so critical?
•Id is directly proportional to W/L. It's not a small correction — it's in the main multiplier.
•A 10% change in L causes a ~10% change in Id. At modern nodes (L = 5–10nm), even 1nm variation is 10–20%.
•This directly shifts the VTC, changes the switching threshold Vm, and changes noise margins.
•In a chain of 1000 gates, each gate has a slightly different Id. Delays accumulate. Timing failures happen.

PART 2 — Sources of Variation: Oxide Thickness
Second source of variation. This one is different — it doesn't change the shape of the transistor.
It changes the gate oxide layer — the extremely thin insulating layer between the Poly gate and the silicon channel.

Quick Recap — What is the Gate Oxide?
•The gate oxide is a layer of SiO2 (silicon dioxide) grown on the silicon surface.
•It sits between the Poly gate (top) and the silicon channel (bottom).
•It is the insulator that makes a MOSFET a voltage-controlled device.
•Thickness = t_ox. In modern nodes, t_ox is only a few atoms thick (1–3 nm in sky130 it's ~4nm).

6.  How Oxide Thickness Affects the Transistor
The gate oxide thickness t_ox appears in Cox:

Cox  =  epsilon_ox / t_ox

•epsilon_ox:  permittivity of SiO2. This is a material constant — it doesn't change.
•t_ox:  oxide thickness. This DOES vary slightly during fabrication.

And Cox feeds directly into the drain current:

Id  =  u Cox (W/L) [(Vgs − Vt)Vds − Vds²/2]

By Observation:
•If t_ox increases slightly (thicker oxide) → Cox decreases → Id decreases → transistor is weaker.
•If t_ox decreases slightly (thinner oxide) → Cox increases → Id increases → transistor is stronger.
•Oxide thickness variation causes the same kind of Id scatter as etch variation — just through a different path.

WHY does oxide thickness vary?
•Oxide is grown by exposing silicon to steam or dry oxygen at high temperature (thermal oxidation).
•The growth rate depends on temperature, gas flow, and silicon surface quality.
•Temperature across the furnace tube is not perfectly uniform — hotter spots grow thicker oxide.
•The same wafer can have slightly different t_ox at the centre vs the edge.
•Wafer to wafer variation also exists depending on load and gas flow in the furnace.

7.  Oxide Thickness Also Shifts the Threshold Voltage Vt
There's a second effect that makes oxide variation even more damaging.
t_ox also affects the threshold voltage Vt — not just Cox.

Vt  =  Vt0  +  gamma (sqrt(|2*phi_F + Vsb|) − sqrt(|2*phi_F|))

Even without the body effect, Vt0 itself depends on flat-band voltage and depletion charge:

Vt0  =  Vfb  +  2*phi_F  +  Qd / Cox

•Qd:  depletion charge. Fixed by doping.
•Cox:  gate oxide capacitance. Depends on t_ox.

So if t_ox changes:
•Cox changes → the Qd/Cox term changes → Vt0 shifts.
•Thicker oxide → lower Cox → larger Qd/Cox → higher Vt → transistor turns on later → Id drops even more.
•Thinner oxide → higher Cox → smaller Qd/Cox → lower Vt → transistor turns on earlier → Id increases.

WHY is this double-hit so dangerous?
Etch variation changes W/L → affects Id through one path.
Oxide variation changes Cox AND Vt → affects Id through TWO paths simultaneously.

•Transistors across the chip all have slightly different Id values.
•The VTC of each gate shifts slightly.
•Switching thresholds Vm, noise margins NMH and NML — all vary from gate to gate.
•This is why designers add margin. You can't count on a perfect VTC.

8.  How These Variations Combine
In a real chip, both types of variation happen at the same time.

•Etching variation:  changes L and W → changes W/L → changes Id.
•Oxide thickness variation:  changes t_ox → changes Cox and Vt → changes Id (doubly).

The total variation in Id from all sources can be significant — easily ±10–20% in older nodes, even more in advanced nodes.

This is why fabrication engineers spend enormous effort:
•Controlling etch uniformity across wafer → tighter L distribution
•Controlling oxidation temperature uniformity → tighter t_ox distribution
•Using optical proximity correction (OPC) → pre-distorting the mask so the etched result comes out right
•Using dummy poly fills → creating symmetric environments for all gates, not just middle ones

9.  Summary — Why Variation Matters for CMOS Inverter Robustness
All of this connects back to what we started studying — CMOS inverter robustness.

•The CMOS inverter only works well if its VTC has the right shape.
•Noise margins NMH and NML depend on VOH, VOL, VIH, VIL — all of which shift when Id changes.
•If Id varies because L varies (etch) or t_ox varies (oxide), the VTC moves.
•In the worst case, noise margins shrink to zero — the inverter fails to correctly reject noise.

That's the real danger of device variation. It doesn't just slow chips down — it can make them wrong.

Key Equations to Remember:
Id  =  u Cox (W/L) [(Vgs − Vt)Vds − Vds²/2]
Cox  =  epsilon_ox / t_ox
Vt0  =  Vfb  +  2*phi_F  +  Qd / Cox

Etch variation → L shifts → W/L changes → Id changes.
Oxide variation → t_ox shifts → Cox changes AND Vt changes → Id changes twice over.


........................................................................

# lecture 45

1. Single Inverter
Before we go into sources of variation we need to understand the basic circuit we are working with which is the Single Inverter.This is the most fundamental gate in CMOS circuit design and it is built using one PMOS and one NMOS transistor connected together.

<img width="525" height="388" alt="image" src="https://github.com/user-attachments/assets/f6c5d6bb-2176-4642-9f87-69a8c91bef40" />

From above picture we can observe the basic symbol of single inverter.It takes In as input and gives Out as inverted output.The Vdd is connected at top which is supply voltage and Vss is connected at bottom which is ground.The circle at the output of the triangle symbol indicates inversion.

Now when we expand this inverter symbol into its transistor level schematic we can see whats happening inside.

<img width="688" height="400" alt="image" src="https://github.com/user-attachments/assets/7e0d296c-b009-4a82-b540-998ae10766d8" />

From above image we can observe:
The Poly Gate(red) is the common gate for both PMOS and NMOS.It is connected to the In signal.This gate decides which transistor is ON and which is OFF.
The PMOS transistor is at the top connected to Vdd with P Diff(green) as its difusion region.When input is LOW the PMOS turns ON and pulls output to Vdd which gives HIGH output.
The NMOS transistor is at the bottom connected to Vss with N Diff(yellow-green) as its difusion region.When input is HIGH the NMOS turns ON and pulls output to Vss which gives LOW output.
The output is taken from the node connecting Drain of PMOS and Drain of NMOS together.

So the inverter works by complementary action of PMOS and NMOS.When one is ON other is OFF.This is why CMOS(Complementary MOS) consumes very low static power because at no point both transistors are ON at same time in ideal case.

1.1 Internal Structure of NMOS in Inverter
Now if we zoom in further into the NMOS transistor which is circled in the schematic we can see the actual physical device structure.This helps us understand where the oxide thickness tox comes in.

<img width="713" height="400" alt="image" src="https://github.com/user-attachments/assets/976e29d2-353e-4e3d-a618-6d16b47a9aa3" />










































































   


























 





   

   
   


   
   










   












   



  






 


 
 


   
   


   

    
  
     
       



   


   







  


   
 




 







  

  

  




 


      

  






  
  

    
 

