Alert Module
============

OP5 Log Analytics allows you to create alerts, i.e. monitoring
queries. These are constant queries that run in the background and
when the conditions specified in the alert are met, the specify action
is taken. For example, if you want to know when more than 20
„status:500" responscode from on our homepage appear within an one
hour, then we create an alert that check the number of occurrences of
the „status:500" query for a specific index every 5 minutes. If the
condition we are interested in is met, we send an action in the form
of sending a message to our e-mail address. In the action, you can
also set the launch of any script.

To go to the alert windows, select the tile icon from the main menu
bar and then go to the „Alerts" icon (To go back, go to the „Search"
icon).

![](/./media/media/image38.png)

We will display a page with tree tabs: Create new alerts in „Create
alert rule", manage alerts in „Alert rules List" and check alert
status „Alert Status".

In the alert creation windows we have an alert creation form:

• Name -- the name of the alert, after which we will recognize and
search for it.

• Index pattern -- a pattern of indexes after which the alert will be
searched.

• Role -- the role of the user for whom an alert will be available

• Type -- type of alert

• Description -- description of the alert.

• Example -- an example of using a given type of alert. Descriptive
field

• Alert method --the action the alert will take if the conditions are
met (sending an email message or executing a command)

• Any -- additional descriptive field

In the alert management window, you can activate / deactivate, delete
and update alerts by clicking on the selected icon with the given
alert. ![](/./media/media/image63.png).

In the alert status window, you can check the current alert status: if
it activated, when it started and when it ended, how long it lasted,
how many event sit found and how many times it worked.
