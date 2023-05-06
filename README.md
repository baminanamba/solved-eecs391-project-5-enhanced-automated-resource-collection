Download Link: https://assignmentchef.com/product/solved-eecs391-project-5-enhanced-automated-resource-collection
<br>
<strong><u>Programming 5: Enhanced Automated Resource Collection</u></strong>.

Use the midas*BuildPeasant config files for this assignment. This is a continuation of resource collection. Now suppose you have an additional action, BuildPeasant (the Townhall can execute this action). This action requires 400 gold and 1 food. The Townhall supplies 3 food and each peasant currently on the map consumes 1 food. If successful, this operator will deduct 400 gold from the current gold tally and result in one additional peasant on the map, which can be subsequently used to collect gold and wood. Since your planner is a simple state space planner, it only produces sequential plans, which will not benefit from the parallelism possible with multiple peasants. To solve this, define additional actions as follows. Write additional Move, Harvest and Deposit operators, Move<em><sub>k</sub></em>, Harvest<em><sub>k</sub></em> and Deposit<em><sub>k</sub></em>, that need <em>k</em> peasants to execute and have the effect of <em>k</em>=1 to 3 parallel Moves, Harvests and Deposits, but will only add the cost of a single action to the plan. To execute such operations, your PEA should then find <em>k</em> “idle” peasants and allocate them to carrying out the Move<em><sub>k</sub></em>, Harvest<em><sub>k</sub></em> and Deposit<em><sub>k</sub></em> operator by finding the nearest goldmine/forest/townhall to go to. Note that your PEA can further heuristically parallelize your found plans, though this reduction in cost cannot be accounted for by the planner. For example, with 3 peasants, suppose you have a Move<em><sub>1</sub></em>(townhall,goldmine) and a Move<em><sub>2</sub></em>(townhall,forest) in sequence. Your PEA can parallelize these actions to execute at the same time by noticing that their preconditions can be simultaneously satisfied. This sort of  behavior by the execution agent falls under scheduling, a part of automated planning that we did not discuss in class. Be careful when writing heuristics for the BuildPeasant operator. Note that it has an immediate negative effect, i.e. it moves the plan farther from the goal. Somehow your heuristic needs to trade this off against the longer-term positive effect that the parallelism will allow.

(a) Set the goal state to be a gold tally of 1000 and a wood tally of 1000. Produce a plan and execute it in SEPIA. (b)  Set the goal state to be a gold tally of 3000 and a wood tally of 2000. Produce a plan and execute it in SEPIA. In each case, output the total time taken to actually execute the plan found. As before, be careful not to “pre-plan” by using your knowledge of the game.

If you feel ambitious, think about how to incorporate an additional action, BuildFarm. This action creates a new Farm that supplies additional food, which can be used to build even more peasants. At this point, however, you will need a proper scheduler to handle the parallelized action dispatching at each time step.

We will award up to 10 bonus points for well written code that is able to quickly find a short plan so that  the total runtime is fast relative to the rest of the class (e.g. if you are in the top three runtimes to finish a scenario with a fixed large resource target). Note that we will test your code with other maps than the ones provided with this assignment.

As a reminder, you should no longer use csevcs. You should turn in your agents (only) in a zip file on canvas by 11:59pm on the due date. No partial intermediate submissions or READMEs are required (you are welcome to include a README if you did anything beyond what the exercise asks you, such as trying BuildFarm, to let us know your observations, but it is not required).