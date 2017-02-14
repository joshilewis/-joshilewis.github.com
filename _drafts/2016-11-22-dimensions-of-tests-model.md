=The Dimensions of Tests Model=

**TL;DR:** Software developers often decide what tests to write based on technical aspects. Instead they should decide what tests to write based on what feedback is missing. The Dimensions of Tests Model can be used to make better decisions around what tests to write.  Useful dimensions to use when deciding what type of tests you should write are primarily: speed of feedback, coverage, longevity and variation.  

--------
The current thinking in the software development industry is to have a lot of low-level unit tests, fewer integration tests, and fewer still, higher-level tests like system tests. The Test Pyramid, shown below, is a common model used to describe the relative amounts or ratios of the different types of tests we should aim for. 

![The traditional Test Pyramid](traditional-test-pyramid.png)

This kind of thinking generally focuses on how quickly the tests run - i.e. speed of feedback - and also how easy it is to write the different types of tests. Both of these are technical considerations. The problem I have with this thinking is it ignores the primary reason we have tests in the first place - to get feedback about our system. If technical considerations govern the types of tests we have, there may be a large number of tests we will never write, and thus a lot of feedback we're not getting. For example, having lots of low-level unit tests doesn't give us any information about how the components in a system work together as a whole. Evidence of this phenomenon is the multitude of memes around unit testing not being enough. Some of my favourites (click the pictures for the original Tweets):  

<a href="https://twitter.com/kentcdodds/status/628658648001048577"><img src="https://pbs.twimg.com/tweet_video_thumb/CLlxtWaUMAAVBKv.png" alt="Unit testers be like" width="274" height="200" /></a>

<a href="https://twitter.com/timbray/status/822470746773409794"><img src="https://pbs.twimg.com/media/C2oAur4UcAE-QaF.jpg" alt="Two unit tests, no integration tests." width="274" height="192" /> </a>

<a href="https://twitter.com/DJDoubleH/status/830125246648872960"><img src="https://pbs.twimg.com/tweet_video_thumb/C4UyJv4WYAAerIp.jpg" alt="there is no functional purpose for this but I would never throw it away" width="274" height="274" /> </a>

<a href="https://twitter.com/withzombies/status/829716565834752000"><img src="https://pbs.twimg.com/ext_tw_video_thumb/829716507752017920/pu/img/YkBai4ApoXBdAkOK.jpg" alt="Unit tests pass, no integration tests" width="274" height="274" /> </a>

Focusing on technical considerations only leads us to make blind trade-offs: we're not even aware of other dimensions we should be considering when deciding which tests to write. The Dimensions of Tests Model was developed to make other dimensions explicit and to help teams make better trade-offs around the types of tests they write. The model is predicated on the idea that *different tests are valuable to different audiences at different times, for different reasons*.

The dimensions currently in the model are:  
 * **Speed**: How quickly does the test execute? How long do we have to wait to get the feedback the test gives us?   
 * **Coverage**:  How much of the system (vertically) does the test exercise? In general, the higher the coverage, the more confident we are about the behaviour of the system as whole. Also known as *scope* or *depth*. 
 * **Variation**:  How many near-identical variations of the test are there? E.g. if a test has lots of inputs, there may be very many combinations of inputs, with each combination requiring its own test. ([This article](http://blog.thecodewhisperer.com/permalink/integrated-tests-are-a-scam-part-1) is useful for more on this idea.)

In an ideal world, our tests would execute instantaneously, cover the entire system, and would deal every combination of inputs and states as well. Therefore, the ideal test would score very highly in all dimensions. Unfortunately this is not possible in the real world since some of the dimensions have an inverse affect on others. The image below is a causal loop diagram showing the causal relationships between dimensions.

![Causal Loop Diagram](dimensions-of-tests-causal-loop.png)

 * An increase in *Coverage* generally leads to a decrease in *speed of feedback*. This is because the more of the system covered by the test, the longer the test takes to run.   
 * An increase in *Variation* typically leads to a decrease in coverage. With high variation, there is usually a very high number of tests. If the suite of tests is to complete running in a reasonable timeframe, we usually decrease the coverage of these tests.  

As the model shows, no test can ever maximise for all dimensions. Any test will compromise on some of the dimensions. We therefore need to choose which dimension to prioritise for a test. This is the trade-off. Each test should prioritise one of the dimensions. The trade-off of priorities should be based on what feedback about the system we need. 

For example, if we need tests that give us information about the behaviour of the whole system, which will be valuable for a long time, we're most likely willing to compromise on speed of execution and variation. The trade-off is now explicit and *deliberate*. Traditionally we would have ruled out such a test immediately because it would take too long to run.

The way I'd like to see the model being used is for teams to decide what system feedback they're missing, decide what trade-offs to make, and then what kind of tests to write.

I believe this to be the the first iteration of the model, I expect it to evolve. I'm certain there are other dimensions I haven't yet included, perhaps even more important dimensions. What dimensions do you use when deciding what type of tests to write? What dimensions do you think should be added to the model? 