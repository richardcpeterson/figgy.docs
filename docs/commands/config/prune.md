
## Prune

Usually leveraged after running sync, prune will compare your desired state as defined in your 
figgy.json with the current configurations in AWS Parameter Store. You will be prompted on whether or not you wish to 
delete stray configurations (configs that exist in AWS but do not exist in your figgy.json file).

Pruning is essential to maintaining a healthy Fig tree!

<br/>
<video autoplay loop muted class="video"><source src="/images/videos/prune.mp4" type="video/mp4"></video>
<br/>