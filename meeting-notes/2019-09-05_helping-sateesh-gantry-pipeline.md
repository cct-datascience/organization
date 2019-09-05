# How can we help Sateesh - 2019-09-05

Participants: Eric, Sateesh, Chris, Julian

Special guest appearance: Nirav

S: Wants to focus on the Makeflow things, needs containers

C: Suggests using 'dummy' containers which just say 'run successfully'

E: Wants to dump large amount of Bayer data sets to test triggering workflow

- [ ] Someone (Eric/Julian/Sateesh?) to talk to Tony about creating IRODS rules

E: Chris & Julian should know how to create IRODS rules

Question: Once the containers are integrated into the DE, and the CWL description is done, will the Makeflow engine:

1. Call the DE API to run the workflow step, or
2. Submit the container step directly to the HTCondor cluster

Nirav shows up!

N: For large workflows, don't bother with rules

N: Let transfer process trigger the workflow on successful completion of the transfer, don't bother with a rule

N: Look at how to consolidate your data (e.g. batching by hour, in a 'packet'). Makes it possible to benefit from parallel transfers, etc.

C: Thinks this already happens with Globus

N: IRODS also batches things (-b flag), but also every file should have a batch 'flag'. Packets also mean you don't have to have thousands of files.

N: Controller of workflow should be controlling & triggering things. So transferring should also be a workflow. 

E: Where is that?

N: Controller can live on a VM, not required to be high-powered. Just tells workers (when they call back) where to get the data and what to do.

E: Future. Parker has bought gantry. What's the simplest thing?

N: What machine is handling the transfer?

C: Gantry cache has a server.

N: Throw away Globus rube-goldberg device. No Globus on our infrastructure.

J: So we would install icommands on cache server?

N: Yes, install icommands on the cache server.

E: When we want to run stuff in CyVerse, as a 'Powered-by-CyVerse' project, what is the best way to run that?

N: Depends on how much computation is required.

E: How much?

C: Can't remember.

S: For the sample run, about five hours.

N: Can use Atmo nodes for workers. Chris, you have access to the OpenStack, right? You can use the cloud infrastructure as well as the local HPC.

N: API is used to trigger/launch something. Not good for anything except for launching jobs inside our compute. Won't be able to launch it on TACC, etc. if you do.

N: With new DE version, you could in theory run the workflow controller as a persistent app.

N: For the processing, DE API might not be a good idea. But good for kicking off a Jupyter notebook to see the progress of a workflow.

E: Would you run this on the HTCondor pool?

N: No, just run it on Atmosphere/Tombstone/Jetstream/UA HPC. Gives you the larger scalability.

E: If you just want to run one program on a single data set?

N: Just run Makeflow without workers. First step is to write the Makeflow workflow. It will handle failures, checkpoints, retries, etc.

E: Was thinking we could start with simple script, but you're saying go straight to workflow.

N: You'd have to go to workflow eventually, so just start with that.

E: Who to talk to?

N: Talk to Tony for IRODS (even though rules not necessary) and Upendra because he has experience with Ansible deploying Workqueue workers.










