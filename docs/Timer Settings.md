A time-driven activity's timer can be configured in five different modes: starts with host, continuous, daily, weekly, or monthly.

??? dps-example "Example"
    An activity set to "weekly" will have its timer tick on the selected day every week and will execute at the same time every N weeks.

    Timer settings can be adjusted in the following ways:  
    - Set the timer mode  
    - Set the base start date/time  
    - Set the base date/time timezone  
    - Set the reoccuring time interval  

By default, the base time/date field is the selected timezone. Note that this is independent of daylight saving time in your location.

---
For the timer settings of a time-driven activity or agent, you can specify the timer mode, define the base date/time when to start, the time zone for the base date/time and the reoccurring time interval. The value for Base time/date field depends on the selected time zone that means that the time is the local time of this time zone.

By default, when you add a new time-driven activity or agent, the time mode is set to “continuous”, the base date/time is set to the current time and date and the time zone is set to “Local Server Time”. To change the default timer mode value, select the Process tab and in the Timer settings area change the timer mode by selecting one of the following modes:

### Starts with host

Select this option to start the activity when the host is started and repeat the processing after a specified number of seconds, minutes or hours.
If wanted, you can configure repeatability for restarting the activity after a certain number of seconds, minutes or hours. Enter a numerical value or use the UP and DOWN ARROW to set the value and select the unit, seconds, minutes or hours, from the drop-down list. Select “Never” from the drop-down list, in case you want to start the activity only once. By default, the recurrence is set to 1 minute.

### Continuous

Select this mode to set a point of time on a specified day to start the activity. To set the date and time when to start the activity, click the calendar button for Base Date/Time and select a date. After the date is selected, the full hours of the day are listed to be selected. After a full hour is selected, you can change the current time by selecting the minutes that are available as 5 minutes intervals. The final date and time is then displayed in the Base Date/Time field.

If needed, change the time zone that is set to “Local Server Time” by default.
You can configure repeatability for restarting the activity after a certain number of seconds, minutes or hours. Enter a numerical value or use the UP and DOWN ARROW to set the value and select the unit, seconds, minutes or hours, from the drop-down list. Select “Never” from the drop-down list, in case you want to start the activity only once. By default, the recurrence is set to 1 minute.
### Daily

Select this mode to start a time-driven activity on a daily basis. To set the date and time when to start the activity, click the calendar button for Base Date/Time and select a date. After the date is selected, the full hours of the day are listed to be selected. After the full hour is selected, you can change the current time by selecting the minutes that are available as 5 minutes intervals. The final date and time is then displayed in the Base Date/Time field.

If needed, change the time zone that is set to “Local Server Time” by default.
You can configure repeatability for restarting the activity, for example, every day or every third day. Enter a numerical value or use the UP and DOWN ARROW to set the value. Select “0”, in case you want to start the activity only once for the specified date and time.
### Weekly

Select this mode to start the activity on a weekly basis. To set the date and time when to start the activity, click the calendar button for Base Date/Time and select a date. After the date is selected, the full hours of the day are listed to be selected. After the full hour is selected, you can change the current time by selecting the minutes that are available as 5 minutes intervals. The final date and time is then displayed in the Base Date/Time field.

If needed, change the time zone that is set to “Local Server Time” by default.
You can configure repeatability for restarting the activity, for example, every week or on Tuesdays every third week. Enter a numerical value or use the UP and DOWN ARROW to set the value after how many weeks the activity is restarted. Select “0” for the week, in case you want to start the activity only once for the specified date and time. To specify a certain day within the week to restart the activity as wanted, click Days to run and select the weekdays.

### Monthly

Select this mode to start a time-driven activity on a monthly basis. To set the date and time when to start the activity, click the calendar button for Base Date/Time and select a date. After the date is selected, the full hours of the day are listed to be selected. After the full hour is selected, you can change the current time by selecting the minutes that are available as 5 minutes intervals. The final date and time is then displayed in the Base Date/Time field.

If needed, change the time zone that is set to “Local Server Time” by default.
You can configure repeatability for restarting the activity, for example, on February, 2nd every year or on the third Tuesday every month. To specify a certain day of a month, select Day from the Mode drop-down list, then select the month from the Month to run drop-down list and finally, the date within a month. Note that the Days to run drop-down list may list more days then the selected month provides. Please ensure that the day selected for the Days to run drop-down list is available for the month selected for the Month to run drop-down list, otherwise the activity is not restarted.

The selected month and days are listed above the drop-down list and provide a Delete button. To remove the selection for a month or day, click the Delete button or click the DOWN ARROW for the drop-down list to clear the selection for the corresponding month, respectively, day.  


!!! dps-note "Important"
    Restarting the activity host does neither change the reoccurring interval nor runs the activity again for the same day. For instance, configuring to run every 2nd week and restarting the [[Activity Host|activity host]] in the second will will not change the execution behaviour.
