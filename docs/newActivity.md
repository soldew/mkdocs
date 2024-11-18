# DocProStar: Create a new activity


!!! dps-tip "DocProStar-SDK"
	This repository provides some help and sample code for using the DocProStar SDK.
	If you have any questions, pleaes contact the product or development department of TCG Informatik AG.

``` py hl_lines="2 3" title="Sort your parameters"
def Set_Items(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]: # (1)
                items[j], items[j + 1] = items[j + 1], items[j]
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.
	
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
	

