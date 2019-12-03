Readme file for use of the usbs.dll with test application.
Ver 0.1 Last saved Date: 9/3/2001 7:09 PM

The test application demonstrates how to the use of usbc.dll to create user application to control 
the USB robot controller.
 If you run this program, or modify it,  you are taking full responsibility for all consequence. 

1.	Safety first !
1.1.	Using the sample application, or writing code for the usbc.dll is extremely dangerous.  It  
provides direct access to internal control  function, optionally bypassing software safety 
features. 
1.2.	Do not use this program if you are not authorized to do so !
1.3.	Do not use this program if you do not fully understand and comply with all safety 
instructions and pre requests. 
1.4.	Always follow all safety instructions provided with you robot.  
1.5.	Use extreme care to protected yourself and others from injury, and to avoid damage. 
1.6.	Insure the robot work envelope is well protected, and be prepared to any sudden 
movements of the arm.
1.7.	Place the Emergency button in reach, and always be ready to immediate use it to stop the 
controller in case of software malfunction. 
1.8.	Learn the detail of the sample code provided, and be sure you fully understand each 
function before you use it.   

2.	Pre requirements : 
2.1.	Installed Scorbase for ER-4u version 4.0, and working ER4u robot, with USB controller.
2.2.	Installed Visual Studio 6.0 including C++, (service pack 5 recommended) .
2.3.	in depth knowledge of  C++ Programming using  VS 6 and MFC.
2.4.	Full knowledge of safety and  operating instructions of the ER-4u controller and arm.
2.5.	The DemoApp1.zip file, opened into am empty directory. 

3.	Overview  of operating the demo : 
3.1.	Insure proper operation of  robot using Scorbase ver 4.0 then exit Scorbase.
3.2.	Open the project "ManualMove.dsw" and run it in VS .
3.3.	Click "Initialization" to turn on power.   (The power led should turn green).
3.4.	Answer Yes to set Control ON: 
3.5.	Open and close the gripper.
3.6.	Select speed 1
3.7.	Select  axis 1
3.8.	Click and hold  "Plus" for short time. The robot arm will move until you release it. 

4.	Code Overview.
4.1.	The project is a standard MFC project, created by the wizard.  The File 
"ManualMoveDlg.cpp" does most of the actual work:
4.1.1.	CManualMoveDlg::OnInit() Is called by the initialization button. It initialize the dll, and 
provide 2 callback functions : one for "init done" message, and one for response 
messages from the dll to the application.
4.1.2.	CManualMoveDlg::OnCon() is called by the "control ON" button. It activate the 
"Control" function in the usbc.dll, with flag '&' for all axes, and TRUE for CON.
4.1.3.	OpenGripper(); is called to open the gripper.
4.1.4.	CManualMoveDlg::RunManual is called by the Plus and Minus click down.  It starts 
internal timer, set the usbc.dll to manual movement by encoder mode , and move the 
requested axis in the requested speed (negative speed reverse movment direction)
	EnterManual(MANUAL_TYPE_ENC);		
	MoveManual((unsigned char)m_iCurrAxis, m_iComboSpeed * 10

4.2.	The file usbc.h in the usbc directory includes definition for all available functions.




