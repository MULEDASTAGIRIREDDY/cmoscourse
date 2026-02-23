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

   # Introduction — Why the Switch Model?

   Before we study SPICE simulations or I-V curves in detail, we need to understand the basic switching behaviour of the CMOS inverter. The MOSFET switch model is a simplified but very powerful way to understand how digital logic works without solving complex equations.

The switch model says: a MOSFET is either fully ON (closed switch with finite resistance) or fully OFF (open switch with infinite resistance). This depends only on whether |Vgs| is above or below the threshold voltage |Vt|.

1. The MOS Transistor Symbol

   <img width="700" height="375" alt="image" src="https://github.com/user-attachments/assets/f9709a16-743b-4e13-9de7-0a394e4bce64" />
   Figure 1 – MOS transistor symbol showing Gate (G), Source (S), Drain (D), and gate-source voltage |Vgs|

The MOS transistor has 3 terminals:
•Gate (G) — the control terminal. Voltage applied here controls whether the channel forms.
•Source (S) — carriers enter the channel from here.
•Drain (D) — carriers exit the channel here.

The controlling parameter is |Vgs| — the magnitude of gate-source voltage. This is compared against the threshold voltage |Vt| to decide the state of the transistor.

2. Transistor as a Switch

   <img width="700" height="375" alt="image" src="https://github.com/user-attachments/assets/9d95ba9a-32e7-496b-adb1-d7119ea425e1" />

Figure 2 – MOS symbol (left) and switch equivalent (right). Transistor → Switch with infinite OFF resistance and finite ON resistance.


Transistor → Switch
•With infinite OFF resistance when |Vgs| < |Vt|
•With finite ON resistance when |Vgs| > |Vt|

OFF State — |Vgs| < |Vt|
No channel forms between S and D. The transistor is in the cutoff region. Resistance between S and D is effectively infinite. The switch is OPEN. No current flows regardless of Vds.

ON State — |Vgs| > |Vt|
A conducting channel forms. The transistor is ON. Finite resistance exists between S and D. The switch is CLOSED with a series resistor. This resistance is called the ON resistance.

WHY is this useful?
In digital circuits we only care about two output states — HIGH (near Vdd) or LOW (near 0). The switch model captures this without needing the full I-V curves. It is much faster for understanding logic behaviour and delay intuitively.


3. The CMOS Inverter Circuit

   <img width="700" height="438" alt="image" src="https://github.com/user-attachments/assets/60f1b250-9f70-4258-8a2f-444743a20b77" />
   Figure 3 – CMOS inverter schematic: PMOS source at Vdd, NMOS source at Vss, both gates driven by Vin, Vout at common drain node (~2:00)
The CMOS inverter has exactly 2 transistors:
•PMOS — source tied to Vdd, gate at Vin, drain at Vout
•NMOS — source tied to Vss (ground), gate at Vin, drain at Vout
•Load capacitor CL at output — models the input capacitance of the next gate

Both gates are driven by the same Vin. The output Vout is taken at the common drain node between the two transistors.

WHY is PMOS source at Vdd?
Because VgsP = Vin - Vdd. For PMOS to turn ON, VgsP must be sufficiently negative, i.e., Vin must be significantly below Vdd. Tying the PMOS source to Vdd ensures this condition is checked correctly.

WHY is NMOS source at Vss?
Because VgsN = Vin - Vss = Vin. For NMOS to turn ON, VgsN must exceed Vtn. Tying the source to ground means VgsN = Vin directly, so the NMOS turns ON when Vin exceeds Vtn.

4. Case 1 — Vin is HIGH (Vin = Vdd)
 <img width="700" height="438" alt="image" src="https://github.com/user-attachments/assets/06f4593d-6c50-4fe3-8c0c-45d4740e73f6" />

 By Observation:
For PMOS:   VgsP = Vin - Vdd = Vdd - Vdd = 0 V
Since |VgsP| = 0 < |Vtp|  →  PMOS is OFF (open switch)

For NMOS:   VgsN = Vin - Vss = Vdd - 0 = Vdd = 2 V
Since VgsN = 2 V > Vtn  →  NMOS is ON (closed switch with resistance Rn)

<img width="700" height="475" alt="image" src="https://github.com/user-attachments/assets/1c5cb835-cdad-4481-9c0b-a3ecb04b9c79" />
Figure 5 – PMOS turns OFF (open switch, left) and NMOS turns ON (closed switch with Rn, right) when Vin = Vdd 

Equivalent Circuit for Vin = Vdd
<img width="700" height="475" alt="image" src="https://github.com/user-attachments/assets/5d2bdf96-8a04-4caa-b501-b701fbac22c5" />
Figure 6 – Equivalent circuit: PMOS is open switch, NMOS is resistor Rn to Vss. Vout discharges to 0 V 

The equivalent circuit shows:
•Vdd → open switch (PMOS OFF) → Vout   — no path from Vdd to output
•Vout → Rn (NMOS ON) → Vss = 0 V   — output pulls down to ground

In steady state, PMOS is off so no current from Vdd. NMOS pulls Vout down to 0 V through Rn. CL discharges to 0 V.

Result:   Vin = Vdd (HIGH)  →  Vout = 0 V (LOW)

This is the correct inverter behaviour — a HIGH input produces a LOW output.

At this operating point, PMOS is off and NMOS is in the linear (triode) region — it behaves like a resistor Rn pulling the output to Vss.

5. Case 2 — Vin is LOW (Vin = Vss = 0 V)
By Observation:
For PMOS:   VgsP = Vin - Vdd = 0 - Vdd = -Vdd = -2 V
Since |VgsP| = 2 V > |Vtp|  →  PMOS is ON (closed switch with resistance Rp)

For NMOS:   VgsN = Vin - Vss = 0 - 0 = 0 V
Since VgsN = 0 V < Vtn  →  NMOS is OFF (open switch)

Equivalent Circuit for Vin = Vss
The equivalent circuit shows:
•Vdd → Rp (PMOS ON) → Vout   — Vdd charges output through Rp
•Vout → open switch (NMOS OFF) → Vss   — no path from output to ground

In steady state, NMOS is off so no path to ground. PMOS pulls Vout up toward Vdd through Rp. CL charges up to Vdd.

Result:   Vin = 0 V (LOW)  →  Vout = Vdd (HIGH)

Correct inverter behaviour — a LOW input produces a HIGH output.

At this operating point, NMOS is off and PMOS is in the linear (triode) region — it acts like a resistor Rp pulling the output to Vdd.

6. Summary — CMOS Inverter Switching Behaviour
Truth table by switch model
•Vin = Vdd (HIGH)  →  PMOS OFF, NMOS ON   →  Vout = 0 V (LOW)
•Vin = Vss (LOW)   →  PMOS ON,  NMOS OFF  →  Vout = Vdd (HIGH)

WHY CMOS has zero static power
In both steady-state cases, one transistor is always OFF. This means there is no direct current path from Vdd to Vss at any time in steady state. No DC current flows, so no static power is dissipated. This is the biggest advantage of CMOS over older logic families like NMOS-only or bipolar logic.

ON Resistance and Delay
The ON resistance values Rn and Rp are not equal in general. They depend on:
•W/L ratio of each transistor
•Carrier mobility (electrons in NMOS are faster than holes in PMOS, so Rn < Rp for equal W/L)
•Supply voltage Vdd

The time to charge or discharge CL through these resistances determines the propagation delay of the inverter. This is the same delay that appears in the delay tables (CBUF1, CBUF2) discussed in earlier lectures. By tuning the W/L ratio we can control Rn and Rp, which in turn controls the delay.

Summary — Key Points from This Lecture
•MOSFET acts as a switch: OFF when |Vgs| < |Vt|, ON when |Vgs| > |Vt|.
•PMOS source is at Vdd. NMOS source is at Vss. Both gates driven by Vin.
•Vin = HIGH → VgsP = 0 (PMOS OFF), VgsN = Vdd (NMOS ON) → Vout = LOW.
•Vin = LOW  → VgsP = -Vdd (PMOS ON), VgsN = 0 (NMOS OFF) → Vout = HIGH.
•One transistor is always OFF in steady state → zero static power dissipation.
•ON resistance Rn and Rp control how fast CL charges/discharges → this is the inverter delay.

>>>>>>>>>>>>>>>>>>>>>>>.<head>24</head> PMOS and NMOS Transistor Behaviour in an Inverter<<<<<<<<<<<<<

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
The behaviour studied in this lecture forms the physical foundation for everything that follows in CMOS design. Let us understand why:
Connection to VTC (Voltage Transfer Characteristic)
The VTC curve — which shows Vout vs Vin — is nothing but a graphical representation of what we studied here. When Vin is LOW, Vout is HIGH (PMOS ON, NMOS OFF). When Vin is HIGH, Vout is LOW (PMOS OFF, NMOS ON). The transition between these two states in the middle region is where both transistors are partially ON, and that transition region determines noise margins, gain, and the shape of the VTC.

Connection to DELAY
From our earlier lectures we know that delay depends on how fast the output node charges or discharges. That charging/discharging is done entirely by IdsP (when output goes HIGH) and IdsN (when output goes LOW). So the delay of the inverter directly depends on the drain currents, which in turn depend on VgsP, VgsN, VdsP, VdsN, and the W/L ratios — all of which we labelled in this lecture.

Connection to SPICE Simulations
When we write a SPICE netlist and run a transient simulation of the inverter, SPICE is internally tracking VgsP, VgsN, VdsP, VdsN at every time step, calculating IdsP and IdsN using the model equations, and then solving for Vout at each time step. So the concepts studied in this lecture are literally what SPICE is computing in the background.

Connection to Physical Design (Clock tree, Crosstalk, STA)
In physical design flows, every timing analysis (STA), clock tree synthesis, and crosstalk analysis ultimately comes down to delay calculation, which comes down to drain currents, which come down to VgsP, VgsN, VdsP, VdsN. This is why understanding how PMOS and NMOS switch in an inverter is the absolute foundation of VLSI design.



>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
<head>PMOS/NMOS drain current v/s drain voltage</head>

<img width="700" height="313" alt="image" src="https://github.com/user-attachments/assets/6142ccec-2cb0-4fc9-a4ae-fbd6c15c7a14" />

From above picture we can observe the inverter circuit with all voltage parameters labelled.
VgsP,VgsN,VdsP,VdsN are the controlling voltages for PMOS and NMOS.
IdsP and IdsN are the drain currents of PMOS and NMOS respectively.
In this lecture we will find how IdsN changes with VdsN and how IdsP changes with VdsP.This is called Id vs Vds curve.

By Observation
From the inverter circuit we can directly find all the voltage expresions by observation.

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
From above picture we can observe that the instructor is now plotting NMOS IdsN vs VdsN curve.
From our previous lectures we know that NMOS has two operating regions:
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

Connection to VTC(next lecture):
In next lecture we will superimpose both families of curves on same plot.For each Vin value the NMOS curve(for that VgsN = Vin) and PMOS curve(for that VgsP = Vin - Vdd) are drawn together.Their intersection gives DC operating point.By tracing all such intersections as Vin varies from 0 to Vdd we get full Vout vs Vin curve which is the VTC.

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

In next lecture we will superimpose both curves on same plot and derive complete VTC of CMOS inverter.

...............................................................................................................................................................................................
# Lecture24

1. CMOS Inverter – Circuit Setup
<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/9b0a0395-6a16-4382-ab62-9484e5105ad1" />
Figure 1 – CMOS Inverter circuit with PMOS and NMOS I-V curve families (~0:53)
Before we get into the graphical analysis, we need to understand what the CMOS inverter circuit actually looks like and how the terminal voltages relate to Vin and Vout. This is all just topology — no device equations needed yet.

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

Figure 2 – NMOS IdsN vs VdsN (left) and PMOS IdsP vs VdsP (right) characteristic curves (~1:00)
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

• Vgsp1 = 0 V      →   Vin = 0 + 2 = 2.0 V   (PMOS barely ON)
• Vgsp2 = -0.5 V   →   Vin = -0.5 + 2 = 1.5 V
• Vgsp3 = -1.0 V   →   Vin = -1.0 + 2 = 1.0 V  (transition region)
• Vgsp4 = -1.5 V   →   Vin = -1.5 + 2 = 0.5 V
• Vgsp5 = -2.0 V   →   Vin = -2.0 + 2 = 0.0 V  (PMOS fully ON)

Physical Meaning of the Mapping
This mapping confirms the inverter behavior from the PMOS side:

When Vin = 0: VgsP = -2V. PMOS has large negative gate-source voltage — it is strongly ON and pulls output toward Vdd. Output is HIGH. This is correct inverter behavior for LOW input.

When Vin = 2V (= Vdd): VgsP = 0V. PMOS gate and source are at same potential — it is OFF. NMOS is strongly ON and pulls output to Vss. Output is LOW. Correct behavior for HIGH input.

When Vin = 0.5 V, 1.0 V, 1.5 V: Both transistors conduct simultaneously. This simultaneous conduction in the transition region is what creates the steep, high-gain transition in the VTC. It also causes a brief current spike (short-circuit current) during switching — this is a source of dynamic power loss.

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
6. <img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/fbf4e86f-3cd7-4ac2-8127-84711d5c1018" />

Figure 5 – NMOS curves and PMOS load lines overlaid; intersection points are operating points (~4:00)
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
+If Vtn increases (process variation), what changes? — NMOS curves shift, Vm shifts downward

All of these can be visualized directly on the combined plot — without resolving equations from scratch each time. This is why the graphical I-V approach is taught before any analytical model.

Summary — Key Equations from This Lecture
•VgsN = Vin                           [NMOS gate-source voltage]
•VdsN = Vout                          [NMOS drain-source voltage]
•VgsP = Vin - Vdd                     [PMOS gate-source voltage]
•VdsP = Vout - Vdd                    [PMOS drain-source voltage]
•IdsP = - IdsN                        [KCL constraint at output node]
•Vin  = VgsP + Vdd                    [Vin-to-VgsP conversion]
•Vm   = Vdd/2  (symmetric inverter)   [Switching threshold]


Next Lecture Preview: We will formally define the Voltage Transfer Characteristic (VTC), identify noise margins NMH and NML from the VTC curve, and calculate the unity-gain points VOH, VOL, VIH, VIL. These parameters tell us how robust the inverter is to noise in a real digital system.

.........................................................................................

# Lecture 25

L5 – Step 3: Converting I-V Curves to Load Curves

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/3766d885-ebe9-4033-ba0c-f4f895ad6a74" />

Figure 1 – Recap slide: PMOS curves relabelled with Vin values, VgsP-to-Vin table, and observation equations (~0:33)
In the previous lecture (L4) we observed the voltage relationships in the CMOS inverter circuit and relabelled the PMOS I-V curves with their equivalent Vin values. This lecture takes that one step further.

The goal here is to convert both the PMOS and NMOS I-V curves from their original terminal voltage axes (VdsP and VdsN) to the Vout axis. Once both sets of curves are on the same Vout axis, we can overlay them and find the operating point of the inverter for each Vin.

Step 1 — Converting PMOS Curves to Vout Axis

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/478e92e2-b01c-4e03-90ec-4fb48bf30ccd" />

Figure 2 – PMOS curves (left) being transformed to IdsN vs Vout axes (right) using Vout = Vdd + VdsP (~2:03)
The Conversion Formula
By observation from the circuit, VdsP = Vout - Vdd. Rearranging gives:

Vout = Vdd + VdsP

This formula lets us swap the x-axis of the PMOS plot from VdsP to Vout. Every point on the PMOS curves can now be expressed in terms of Vout.

How the x-axis changes
Before the substitution, the PMOS x-axis ran from VdsP = 0 (at the right) to VdsP = -Vdd (at the left). After the substitution:
•VdsP = 0     →   Vout = Vdd + 0 = 2 V   (right side of the new plot)
•VdsP = -Vdd  →   Vout = Vdd - Vdd = 0 V  (left side of the new plot)

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

All curves start at the right (Vout near Vdd) and fall as Vout moves left toward 0. This is the opposite direction compared to NMOS curves — which rise from the left. That opposing shape is exactly what allows them to intersect and define an operating point.

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

Step 4 — Merging Load Curves and Building the VTC

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/f4493837-aa47-4a0a-9ec3-91b64817bbb7" />

Figure 1 – Both load curves side by side. Centre: NMOS load curve (Vin = 0 bottom, Vin = 2 top). Right: PMOS load curve (Vin = 0 top, Vin = 2 bottom). VTC axes empty at bottom right (~0:35)
In the previous lecture (L5) we converted both the PMOS and NMOS I-V curves into load curves on the same IdsN vs Vout axes. Now we merge them onto a single plot and read the operating points.

The idea is simple:
•For each Vin, there is one NMOS load curve and one PMOS load curve active simultaneously.
•They intersect at exactly one point — that is the DC operating point of the inverter for that Vin.
•Reading Vout at each intersection and plotting (Vin, Vout) builds the Voltage Transfer Characteristic (VTC).

Step 1 — Superimposing Both Load Curves

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/9015dc1d-3d50-4139-9a48-dcde769283fc" />

Figure 2 – NMOS and PMOS load curves merged on one IdsN vs Vout plot. PMOS runs top-right to bottom-left, NMOS runs bottom-left to top-right (~0:50–1:40)
From observation, Vin and Vout are common to both transistors — the same Vin drives both gates, and the same Vout appears at both drains. So for a given Vin:

•One PMOS load curve is active (selected by that Vin value)
•One NMOS load curve is active (selected by that same Vin value)
•The intersection satisfies IdsP = -IdsN, which is the KCL constraint at the output node

The slide states: 'Vin and Vout are common to PMOS and NMOS. Graphically, we will pick up Vin points from the intersection of corresponding load lines.'

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

Figure 4 – Second intersection point: When Vin = 0.5, 1.5 < Vout < 2. VTC dot at (~0.5, ~1.9). PMOS linear, NMOS sat (~2:30–3:20)
Operating Point 2 — Vin = 0.5 V
•NMOS:  VgsN = 0.5 V → slightly above threshold → NMOS barely ON → small IdsN
•PMOS:  VgsP = 0.5 - 2 = -1.5 V → still strongly ON
•Intersection:  Occurs at Vout between 1.5 V and 2 V — approximately 1.9 V
•Region:  PMOS linear, NMOS saturation
•Physical meaning:  PMOS still dominates and holds output near Vdd. NMOS starts to pull down slightly.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/def7cd6d-e138-4254-8666-795bddd29ef5" />

Figure 5 – Third intersection point: When Vin = 1, 0.5 < Vout < 1.5. VTC dot at (~1, ~1). PMOS sat, NMOS sat. VTC now showing steep fall (~3:20–4:10)
Operating Point 3 — Vin = 1 V (Transition Region)
•NMOS:  VgsN = 1 V → moderately ON
•PMOS:  VgsP = 1 - 2 = -1 V → moderately ON
•Intersection:  Occurs near Vout = 1 V — the midpoint
•Region:  PMOS saturation, NMOS saturation
•Physical meaning:  Both transistors are simultaneously conducting in saturation. This is the highest-gain region of the inverter. A small change in Vin produces a large change in Vout here.

<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/dd0253b7-88c7-48bc-91d5-2693d3dc9651" />

Figure 6 – Fourth intersection point: When Vin = 1.5, 0 < Vout < 0.5. VTC dot at (~1.5, ~0.1). PMOS sat, NMOS linear (~4:10–5:00)
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
<img width="738" height="329" alt="image" src="https://github.com/user-attachments/assets/63fd4dc1-3fd5-4863-892c-ef27f6aa21ef" />

Figure 7 – Complete VTC with all 5 operating points plotted and connected. Each point labeled with transistor regions. The S-shaped VTC is now fully derived (~5:00–5:34)
Plotting the 5 operating points on the Vout vs Vin graph and connecting them gives the complete Voltage Transfer Characteristic (VTC) of the CMOS inverter.

Summary table of all 5 operating points
•Vin = 0.0 V  →  Vout = 2.0 V   |  PMOS linear,  NMOS off
•Vin = 0.5 V  →  Vout ≈ 1.9 V  |  PMOS linear,  NMOS saturation
•Vin = 1.0 V  →  Vout ≈ 1.0 V  |  PMOS sat,     NMOS saturation  ← transition region
•Vin = 1.5 V  →  Vout ≈ 0.1 V  |  PMOS sat,     NMOS linear
•Vin = 2.0 V  →  Vout = 0.0 V   |  PMOS off,     NMOS linear

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

..............................................................................................
<head>DAY4</head>

# Introduction to NOisse margin.












   


























 





   

   
   


   
   










   












   



  






 


 
 


   
   


   

    
  
     
       



   


   







  


   
 




 







  

  

  




 


      

  






  
  

    
 

