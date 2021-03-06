## Simple Notification and Feeds System

### Summary
There is currently no way to provide notifications or alerts to users. We need a way for services and platform components to register notifications for the user and a way for the user to see them.

### Story/Description
KBase needs a simple notification system to alert users to changes in job states, new sharing events, and updates to their favorited apps. In the current framework, a user would have to actively look for the state of these events and compare them to what they remember as the previous state. We propose to create a single location on the User's Dashboard that aggregates the notifications. 

#### Notifications
In this initial implementation, notifications will have the following properties: 

* Simple. They will be very simple text messages with an optional link. 
* KBase only. They will be sent only from KBase platform services, not users or contributed SDK apps.
* No priorities. All notifications will arrive with the same priority. 
* Uneditable. We will not support retracting or updating notifications.
* Flat. Notifications will not be grouped, hierarchical, nest or have sub-notifications.
* Unshared. Users cannot share or forward notifications to other users.
* Two states. Notifications can exist as read or unread.

#### Notification Triggers
In the initial implementation, notifications will be triggered by the following events:

* User Jobs. State changes like submitted, running, completed or failed with error.
* Shares. When a Narrative has been shared with the user.
* App updates. For any App in the users favorites list, a notification will be sent when it is updated. 
* Email notification. The triggering event can set a flag to have the notification system email the user. For example, upon submitting a job, the user could check a box asking for an email notification that the job completes. That would set a flag indicating that the notification service should send an email as well as the normal notification.

This would be most likely be implemented as a generic service call that takes as minimal input the sender, receiver and message. It could be adopted by additional KBase platform services, but they are not the initial target.

#### Notification Viewer
A Notification Viewer panel will be added to the user Dashboard. This panel will have the following properties:

* List notifications. Scrollable sorted list of notifications, most recent on top.
* Change notification state. Mark notifications as read.
* Email control. Simple check box controls for allowing the user to receive email notifications on Share and App updates. 
* Filter/Search. Simple text search/filter options.

### User Stories

### Narrative Mockup
N/A

### Timeline
Our approach will be to quickly build out the end-to-end functionality and iteratively evaluate system with stakeholders and expand the feature set.

#### Sprint 1
Build initial prototype with simple, stand alone viewer into ci. Demonstrate creation of notifications, storage and display.

#### Sprint 2
Evaluate prototype with stakeholders. Expand functionality to include the email notifications. Integrate viewer into Dashboard. Connect Jobs, Narratives and Apps to prototype. Document usage of the notification api.

#### Sprint 3
User Testing. Initial release to next. Expand viewer to support the simple controls and make backend services to support it. Begin aggressive stress and performance testing. Finalize documentation of the notification api, initial documentation of the viewer.

#### Sprint 4
User Testing. Release to production. Finalize the documentation of the viewer. Testing, bug fixing

### Test plan
We will follow the KBase conventions for unit tests and attempt to have full code coverage. Our user testing will focus on one-on-one user interviews and observation of usage. Our stress and performance testing will focus on simulating usage.

### Citations
N/A 