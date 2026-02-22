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
  Vgs-V(x) is gte to channel voltage at a given point.




 


      

  






  
  

    
 

