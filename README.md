# Solution Proposal for the Mountkirk Games case study (2021)

## Company overview
Mountkirk Games makes online, session-based, multiplayer games for mobile platforms. They have recently started expanding to other platforms after successfully migrating their on-premises environments to Google Cloud.
Their most recent endeavor is to create a retro-style first-person shooter (FPS) game that allows hundreds of simultaneous players to join a geo-specific digital arena from multiple platforms and locations. A real-time digital banner will display a global leaderboard of all the top players across every active arena.

* ***Notes:***
  * ***online session-based multiplayer games for mobile platforms***
  * ***recently migrated to GCP***
  * ***goal is to enable hundreds of simultaneous players to join a geo-specific digital arena***
  * ***real-time digital banner on a global leaderboard***

 
## Solution concept
Mountkirk Games is building a new multiplayer game that they expect to be very popular. They plan to deploy the game`s backend on Google Kubernetes Engine so they can scale rapidly and use Google`s global load balancer to route players to the closest regional game arenas. In order to keep the global leader board in sync, they plan to use a multi-region Spanner cluster.
 
* ***Notes:***
  * ***game backend on GKE (scale rapidly)***
  * ***Global LB to route players to the closest regional game arena***
  * ***Multiregion Spanner cluster for Global leader board***

## Existing technical environment
The existing environment was recently migrated to Google Cloud, and five games came across using lift-and-shift virtual machine migrations, with a few minor exceptions.
Each new game exists in an isolated Google Cloud project nested below a folder that maintains most of the permissions and network policies. Legacy games with low traﬃc have been consolidated into a single project. There are also separate environments for development and testing.
 
* ***Notes:***
  * ***five games migrated (VM lift-and-shift) to GCP***
  * ***new games separated in projects, below one folder (permissions and policies set on folder level)***
  * ***legacy games (low traffic) merged in one project***
  * ***separated environments for dev and test***

 
## Business requirements
* Support multiple gaming platforms. ***-->  Firebase (https://cloud.google.com/blog/products/gcp/how-to-build-mobile-apps-on-google-cloud-platform )***
* Support multiple regions. ***--> Global LB***
* Support rapid iteration of game features. 
* Minimize latency.
* Optimize for dynamic scaling. ***--> GKE, AppEngine***
* Use managed services and pooled resources.
* Minimize costs. ***--> autoscale***
 
## Technical requirements
* Dynamically scale based on game activity ***--> GKE***
* Publish scoring data on near real-time global leaderboard ***--> Cloud Datastore***
* Store game activity logs in structured files for future analysis ***--> Bigtable***
* Use GPU processing to render graphics server-side for multi-platform support ***--> (https://cloud.google.com/architecture/orchestrating-gpu-accelerated-streaming-apps-using-webrtc)***
* Support eventually migration of legacy games to this new platform
 
## Executive statement
Our last game was the first time we used Google Cloud, and it was a tremendous success. We were able to analyze player behavior and game telemetry in ways that we never could before. This success allowed us to bet on a full migration to the cloud and to start building all-new games using cloud-native design principles. Our new game is our most ambitious to date and will open up doors for us to support more gaming platforms beyond mobile. Latency is our top priority, although cost management is the next most important challenge. As with our first cloud-based game, we have grown to expect the cloud to enable advanced analytics capabilities so we can rapidly iterate on our deployments of bug fixes and new functionality.


![alt text](https://github.com/khelmric/gcp_case_study_mountkirk/blob/main/Mountkirk_Diagram.png?raw=true)
