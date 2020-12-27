1. First entry point is function intercept
2. It will call this function
```
				if (this.spesificOptions?.queueEnabled || this.options.queueEnabled) await this.queueLimiter.removeTokens(1)
```
3. In RateLimiterQueue.js is called removeTokens().  It always hands in ```1```
4. Calls 

# First entry is there is nothing in the queue.
i.  It will call limiterFlexible consume.  
-- TODO add consume function details

Consume has two outsomes
Look at RateLimiterMemory.js for the default response.  There are three outcomes

i. Look at memory storage incrby
Returns RateLimiterRes
- remainingPoints - In current duration
- msBeforeNext - milliseconds before next action
- consumedPoints - consumed points in current duration
- isFirstInDuration

ii. res.consumedPoints > this.points.  It will 

### resolve

### reject

# If the queue is not empty it will call queueRequest.  
_queueRequest will do the following:
i. check if the current queue lenght is less than the maxQueueSize
ii. it it is less than it will push the response into the queue


## queueRequest

-- This is a simple function that just pushes the queue request onto the queue.  If the queue max is too big it will throw a RateLimiterQueueError

## queueRequest.call -> setTimeout


For Queue to get engaged you need the following.  You need to call _queueRequest.  The only way this happens.  Is :
i. queue.length > 0
ii. consume throws an error.  The only way that this will happen
res.consumedPoints > this.points