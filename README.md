Metro Companion is an assistive travel application designed primarily for deaf and hard-of-hearing passengers who may not hear metro announcements and may have difficulty seeing station information displays in crowded trains.
The initial target is Bengaluru Namma Metro, with the long-term goal of supporting metro systems across India.
2. Main features planned

Station and destination selection

Select the boarding station and destination. Display the route and stations remaining.

GPS-based station detection

Estimate the passenger's location and identify the current and next stations using location and route information.

Destination alerts

Display a prominent warning before reaching the destination, with vibration or other alerts where supported.

Announcement recognition

Investigate recognising Kannada and English station announcements as an additional way to confirm the next station.

Offline operation

Store downloaded station and route information on the phone so that core journey information can be available without continuous internet access.



iPhone support

Investigate alerts while the phone is locked and the screen is off. These capabilities must be tested on an iPhone and may require native iOS functionality.


3. Development environment
Item	Current details
Development computer	Windows laptop
Project folder	C:\MetroCompanion
Web prototype	C:\MetroCompanion\web\index.html
Python version	Python 3.11.9
Initial browser	Google Chrome on Windows
Target phone	iPhone
Web server	Python HTTP server, port 8000
Laptop IPv4 address	192.168.31.239

Important constraint: The laptop belongs to your company. Administrator access may be restricted, so the development process should avoid requiring changes to company security settings.
4. Existing project files and work
The following files and components have already been developed or tested during the project.
File/component	Purpose
data\stations.json	Initial sample station data
data\gtfs\	Downloaded Bengaluru Metro GTFS data
data\gtfs\selected_journey.json	Selected journey data
journey_planner.py	Builds a journey from GTFS data
simulate_journey.py	Simulates travel station by station
gps_station_detection.py	Analyses station coordinates and distances
simulate_gps_movement.py	Simulates movement between station coordinates
web\index.html	Browser-based Metro Companion prototype

The GTFS data contains Green, Purple and Yellow Line information. The initial web prototype uses a selected sequence of 15 stations.

Development rule: Keep existing Python scripts unchanged unless a specific change is discussed and approved. Add new functionality separately wherever practical.
5. Current journey used for testing
The prototype uses this example journey:
Sri Sathya Sai Hospital

Starting station

Nallurahalli → Kundalahalli → Seetharampalya → Hoodi → Garudacharpalya → Singayyanapalya → Krishnarajapura → Benniganahalli → Baiyappanahalli → Swami Vivekananda Road → Indiranagar → Halasuru → Trinity


Mahatma Gandhi Road

Destination station

The example contains 15 stations and 14 station-to-station segments.

The intended behaviour is to display a warning when the destination is the next station, followed by a destination-arrival message.
6. Current development status
Completed: Windows web prototype

The page opens in Chrome. Station selection, simulated movement, progress display and destination warnings have been tested.



Completed: Python journey simulation

The existing simulation can move through the selected journey station by station.

In progress: iPhone browser test

The iPhone requested the page and the Python server logged HTTP 200, but Chrome on the iPhone displayed a blank screen. The display issue remains unresolved.

Not yet implemented: live journey tracking

Real-time GPS station detection, actual train-route matching, live announcement recognition, and dependable background destination alerts are not yet implemented in the web prototype.

7. Important technical considerations
1. GPS alone may not reliably identify a station. Nearby stations, underground sections, inaccurate GPS and trains travelling between stations can create uncertainty. The app should avoid displaying a confident destination alert when the location is uncertain.

2. Straight-line distance is not track distance. The earlier coordinate calculations estimate geographic distance between stations; they do not represent the exact train track or prove that a train has reached a station.

3. Locked-screen operation needs separate investigation. A web page may be suspended when the iPhone locks. Reliable background tracking and notifications may require a native iOS app or other iOS-supported capabilities.

4. Announcement recognition is supplementary. Mixed Kannada and English speech can be difficult to recognise correctly. Recognition should not be the only source of destination confirmation.

5. Offline support needs testing. Station data can be stored locally, but features such as live map services or online speech recognition may require internet access.
8. Recommended development sequence
1. Resolve the blank screen on iPhone Chrome while preserving the working Windows prototype.
2. Confirm that the layout and controls work on the iPhone screen.
3. Connect the prototype to the existing journey data without modifying the existing Python scripts.
4. Develop and test real GPS-based station detection and route matching.
5. Add clear visual destination warnings and investigate vibration and notification support.
6. Investigate Kannada/English announcement recognition and offline operation.
7. Test the application during actual journeys before relying on it for travel.
8. Expand to other Indian metro systems after Bengaluru testing is reliable.

Project principle
Safety, accessibility and reliability come first. The app must help passengers know where they are and when to prepare to get off, without giving false confidence when the station or location cannot be identified reliably.

The immediate next task is to diagnose the iPhone blank screen. We should not start implementing GPS or modify the existing Python scripts until the browser prototype is working on both devices.
