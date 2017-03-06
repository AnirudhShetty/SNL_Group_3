G3: Anirudh Shetty, Sarjo Das, Yatindra Shashi.
**********************************************************************Usage**************************************************************************
Imorting the code,
Here,
	1) The code in "Trfc_Cntlr_Cde" folder is downloaded in to motes running as traffic controllers.

	2) The code in "Vehicle_Cde folder" is downloaded in to motes running as vehicles.

	3) A PPP router is used to send UDP commands and monitor the traffic in network.

	4) "Z_FutureWork_GUI_Eval" folder can be ignored for this implementation.


Working,
Basically as the device is booted, it starts sensing for vehicles, and the when the net traffic is going to reach maximum capacity all three LED's light up in vehicles to show the alert.

Here,

	1) The traffic  controllers are asumed to have some reasonable distance between them like 2 feet for example.

	2) The vehicles are passing close by the traffic controller meant to be monitoring it's road.

	3) The pthon script "Listener.py" in  "Trfc_Cntlr_Cde" folder is used to monitor live traffic and alerts.

So, we have to vary the number of vehicles near each traffic controllers and see what is the output to cover different scenarios.

Checking for output, and testing

Here,
	1)There is a no default output on python/ppp terminal which shows live traffic at roads maintained by traffic controllers, it can be used to to send router commands, for example, "help" and\or "read" to see current threshold, or "newthresh X" to set new threshold.

	2) Executing $Python TheftListener.py will show live traffic and divert alerts at roads maintained by traffic controllers. It also gives Alert type and Traffic controller ID for easy identification.

Message format used for python listner to send traffic and alert notification is as below which is sent periodically and also when there is traffic alert respectively.

  "Traffic_Deviated";     -> It is set to 1 when a Traffic deviation alert comes in saying "Traffic is deviated at this road".
                             It is set to 0 for normal traffic report mentioning traffic density at a road.
  "SeqNo";		-> Number used in sync of controller messages.

  "Traffic_controller";	-> Id of the Traffic controller whose traffic report we are looking at.

  "Current_Traffic";	-> The numerical value shows how many vehicles are at a particular road concerned with the traffic controller from above.

  We can see the changes in these value, corresponding to changes in vehicle density and verify the results.


*****************************************************************Router Commands**********************************************************************
Please start with "help", to start seeing the values coming in.

Command : "help" to see the available commands and start using router terminal.

Command :"newthresh X" for setting new threshold value for theft detection.
Format:  "read" -> Give current thresh value.
         "newthresh X"-> sets new threshold value. 
	 "X" is a numerical value here.


Note: Listener.py, and NodeID.py are provided by Devs, and not auto generated using nescc-mig tool from makefile, because of customizations.
******************************************************************************************************************************************************
