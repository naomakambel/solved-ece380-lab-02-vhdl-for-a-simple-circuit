Download Link: https://assignmentchef.com/product/solved-ece380-lab-02-vhdl-for-a-simple-circuit
<br>
<strong>Part I. VHDL for a simple circuit </strong>

The objective of this practice is to generate and simulate (test) different type of design for a simple combinational logic. Please use three individual projects for the following tasks.

<table width="271">

 <tbody>

  <tr>

   <td width="69"><em>a </em></td>

   <td width="36"><em>b </em></td>

   <td width="58"><em>c </em></td>

   <td width="108"><em>f </em></td>

  </tr>

  <tr>

   <td rowspan="2" width="69"> </td>

   <td width="36">0</td>

   <td width="58">0</td>

   <td width="108">1</td>

  </tr>

  <tr>

   <td width="36">0</td>

   <td width="58">1</td>

   <td width="108">0</td>

  </tr>

  <tr>

   <td rowspan="2" width="69"> </td>

   <td width="36">1</td>

   <td width="58">0</td>

   <td width="108">0</td>

  </tr>

  <tr>

   <td width="36">1</td>

   <td width="58">1</td>

   <td width="108">1</td>

  </tr>

  <tr>

   <td rowspan="2" width="69"></td>

   <td width="36">0</td>

   <td width="58">0</td>

   <td width="108">0</td>

  </tr>

  <tr>

   <td width="36">0</td>

   <td width="58">1</td>

   <td width="108">1</td>

  </tr>

  <tr>

   <td rowspan="2" width="69"> </td>

   <td width="36">1</td>

   <td width="58">0</td>

   <td width="108">1</td>

  </tr>

  <tr>

   <td width="36">1</td>

   <td width="58">1</td>

   <td width="108">0</td>

  </tr>

 </tbody>

</table>




<strong>Design A: </strong>Write a VHDL model (entity and architecture) to describe the logic specify by the above truth table. Describe the circuit with AND, OR, NOT in your architecture body.

<ul>

 <li>Create a project using VHDL, following lab 01 related steps.</li>

 <li>Test your design using functional simulations. You need to generate all the combinations for those three inputs, i.e., 000, 001, 010, …,111.</li>

 <li>With a ready VHDL code, compile (short-cut key, Ctrl+K).</li>

 <li>Generate waveform simulations. Follow the same procedure in lab 1 to open .vwf file. List all the input (A, B, C), and output (f) nodes and insert them in the waveform editor. Since there are 3 inputs, number of possible inputs are 2<sup>3</sup>=8.</li>

 <li>Select the signal you want to edit in the waveform editor</li>

 <li>Click the icon “overwrite clock” on the toolbar</li>

 <li>Set the period of signal and click OK. A clock waveform will be generated in the waveform editor</li>

 <li>Set the period of signals A, B and C to 20, 40, and 80 ns respectively. Set the end time to 160 ns.</li>

 <li>Run functional simulations to generate the output waveform and save the screenshot of .vwf showing all the inputs and output.</li>

</ul>

<strong>Note: </strong>Similar tutorial materials can be found in <em>Introduction to Simulation of VHDL Designs,</em> supplement_quartusii_simulation_vhdl.pdf, in lab 01.

<strong>Design B: </strong>Create a schematic based on the NOR gate implementation.

<ul>

 <li>Test/simulate this design.</li>

 <li>Open .vwf and insert the clock signals for A, B, and C inputs as in Designs A and B.</li>

 <li>Perform functional simulations.</li>

 <li>Compare the generated output waveform with those from Designs A and B.</li>

</ul>

<strong>Part II. Generate a flashing LED </strong>

In this part, you are asked to follow a simple design and upload the design to the Altera’s DE1 board. This simple design drives a LED flashing at a rate of one second.

The DE1 board provides 50 MHz clock signals. To generate the required one-second period clock, you need to use a multi-bit counter, which can be implemented by a library module LPM_COUNTER, in Quartus II, to divide the onboard 50 MHz clock. The customized LPM_COUNTER uses 26 bits can count from 0 to 50,000-1. The counter reduces the frequency of the 50 MHz clock signal and its output behaves as a clock signal changing at the rate of one second.

<strong>Requirement: </strong>Demonstrate a LED flashing at 1 second rate.




Step 1: Create a new project named frequency. Under the project, create a new BDF file and save the file as frequency.bdf.




Step 2: Configure lpm_conter and draw the schematics

–     Go to <strong>Library </strong>à Arithmetics à <strong>lpm_Counter</strong>

When you click on lpm_counter, a dialogue window “Save IP variation” appears as below:










Save it under the project ‘frequency’ as lpm_counter1(C:altera16.0quartusfrequencylpm-counter1). Make sure you save it as VHDL and click OK.




After clicking OK, MegaWizard Plug-in manager appears where parameters of the counter can be changed. It goes through the following six steps:




<ol>

 <li>Change the number of bits to <strong>26</strong>, click Next.</li>

</ol>













<ol start="2">

 <li>Insert <strong>50,000,000</strong> as modulus with a count modulus, click Next.</li>

</ol>













<ol start="3">

 <li>Click Next.</li>

</ol>










<ol start="4">

 <li>Click Next.</li>

</ol>
















<ol start="5">

 <li>Select the type of files you want Quartus II to generate. Select “VHDL component declaration file”, “symbol file” and then click Finish.</li>

</ol>













<ol start="6">

 <li>After that, click Yes to add lpm_counter1 file to the existing projects.</li>

</ol>




Once added, lpm_counter1 can be found in the symbol tool and can be dragged on the block editor.




Step3: With lpm_counter1 in the block editor, fetch an Input pin, connect it with lpm_conter1, and name the pin as Clock. Connect the wire on the output side and double click the wire to highlight it into blue. The highlighted blue indicates that the wire can be named. Name it as q[25..0]. Further, name the output pin as q[25].

Step 3: Save and compile the project.

Step 4: Pin assignment. After the project is successfully compiled, assign the DE1 pins to both input and output of your design.

Click on pin planner and the following image appears.

<h1>View of DE 1 board before assigning pins</h1>




Click on location and type in PIN_AF14 to assign pin to clock signal (input) and type in PIN_V16 to assign q[25] (output).




The details of PIN numbers of clock input signal (Page 20) and output (Page 24) can be found in DE1 board manual (distributed along this lab document).







<h1>View of DE 1 board after assigning pins</h1>

<strong> </strong>




Step 5: Compile again and upload the program to DE 1 board

<ul>

 <li>Switch ON the DE1 Board using the red button</li>

 <li>In Quartus II, go to Tools-à Programmerà Hardware Setup-àselect ‘DE-SoC’</li>

 <li>Make sure Mode is ‘JTAG’</li>

 <li>Click auto-detect</li>

 <li>Select 5CSEMA</li>

</ul>







<ul>

 <li>Right click on 5CSEMA5-àadd file-àoutput files-àselect the frequency.sof file (in output files of the directory)</li>

 <li>Click on the Program/Configure checkbox on the 5CSEMA5 line – Click ‘Start’.</li>

 <li>At this point, your program has been transferred to the DE1 board. You should see the LED flashing on DE1 Board.</li>

</ul>













<strong>You can also follow the youtube link for the implementation: </strong>




<a href="https://www.youtube.com/watch?v=sbUAJByFb30">https://www.youtube.com/watch?v=sbUAJByFb30</a>




Note that our Quartus II version is different from the one from the video. You should adjust accordingly, based on the instructions provided above.










<strong>Write the Lab Report: </strong>Please follow the sample report format as in Lab 01 and do the following in the lab report:

<strong> </strong>

<ul>

 <li><strong>Print the source codes/schematics (make sure it is well commented) for Part I and the schematics for Part II. </strong></li>

 <li><strong>Provide waveforms for all designs in Part I. </strong></li>

 <li><strong>Mark the printouts to show each test case for Part I. </strong></li>

 <li><strong>Explain your test procedures for Part I and Part II. </strong></li>

</ul>

<strong> </strong>

<strong> </strong>