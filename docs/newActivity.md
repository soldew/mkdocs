# DocProStar: Create a new activity


!!! dps-tip "DocProStar-SDK"
	This repository provides some help and sample code for using the DocProStar SDK.
	If you have any questions, pleaes contact the product or development department of TCG Informatik AG.

!!! dps-example "Process your root document"
	=== "C#"
		``` c# linenums="1" hl_lines="6 7 8 9" title="C# Process your root document"
		public override void ProcessDocument(DtoWorkItemData workItemInProgress,
											STGDocument documentToProcess)
		{
			foreach(var fields in documentToProcess.Fields)
			{
				foreach (var f in documentToProcess.IndexFields)
				{
					f.FieldValue.Set(true); // # (1)  
				} 
			}
		}

		```  

	=== "Java script"
		``` java linenums="1" hl_lines="6 7 8 9" title="C# Process your root document"
		function reverseString(str) {

			// empty string
			let newString = "";
			for (let i = str.length - 1; i >= 0; i--) {
				newString += str[i];
			}
			return newString;
		} 
		```

	=== "Phyton"
		``` py linenums="1" hl_lines="6 7 8 9" title="C# Process your root document"
			import pandas as pd
			# Read data from a CSV file
			data = pd.read_csv('data.csv')

			# Perform basic analysis
			mean = data['column_name'].mean()
			print(f"Mean: {mean}")
		```  

	=== "Cobol"  

		``` cobol linenums="1" hl_lines="6 7 8 9" title="C# Process your root document"
			*> setup the identification division
            IDENTIFICATION DIVISION.
            *> setup the program id
            PROGRAM-ID. HELLO.
            *> setup the procedure division (like 'main' function)
            PROCEDURE DIVISION.
              *> print a string
              DISPLAY 'WILLKOMMEN'.
            *> end our program
            STOP RUN.

		```

!!! dps-tip "ActivityDebugger"
	Contains C# project, which allows you to start a windows forms application, this will allow you to debug your activity, without attaching to any service.

!!! dps-tip "ActivityPackagingTool"
	Contains a tool, which allows you to create stgpack out of your compiled assemblies. The stgpack can then be registered in the Process Modeler to be used like any other activtiy.

!!! dps-tip "SampleActivities"
	This folder contains two simple activities, both with same functionality from code point of view. The NativeSampleActivity does not have any DPS references, but only Primus (STG) references. The DocProStarSampleActivity gives you some additional goodies, like "Continue On Error" or specific file logging.

!!! dps-tip "CustomMarketPlugIn (Custom Validation Rules)"
	This folder contains a step-by-step introduction how to implement custom validation rules and a c# sample project of a Market Plug-In project.

!!! dps-tip "CustomLookupPlugIn (Data mapping)"
	This folder contains a step-by-step introduction how to implement custom validation rules and a c# sample project of a Lookup Plug-In project.


!!! dps-tip "REST API"
	This folder contains a step-by-step introduction how to user REST calls to upload documents into the DPS platform.
	

