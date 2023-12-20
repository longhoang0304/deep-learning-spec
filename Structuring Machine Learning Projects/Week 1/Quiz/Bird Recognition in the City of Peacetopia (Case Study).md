**Problem Statement**

![](./Images/W1Q1Img1.jpg)

This example is adapted from a real production application, but with details disguised to protect confidentiality.

You are a famous researcher in the City of Peacetopia. The people of Peacetopia have a common characteristic: they are afraid of birds. To save them, you have **to build an algorithm that will detect any bird flying over Peacetopia**  and alert the population.

The City Council gives you a dataset of 10,000,000 images of the sky above Peacetopia, taken from the city’s security cameras. They are labeled:
- y = 0: There is no bird on the image
- y = 1: There is a bird on the image

Your goal is to build an algorithm able to classify new images taken by security cameras from Peacetopia.

There are a lot of decisions to make:
- What is the evaluation metric?
- How do you structure your data into train/dev/test sets?

**Metric of success**

The City Council tells you that they want an algorithm that
1. Has high accuracy.
2. Runs quickly and takes only a short time to classify a new image. 
3. Can fit in a small amount of memory, so that it can run in a small processor that the city will attach to many different security cameras.


**1. Having three evaluation metrics makes it harder for you to quickly choose between two different algorithms, and will slow down the speed with which your team can iterate. True/False?**
- [x] True
- [ ] False


**2. The city revises its criteria to:**
  **- We *need* an algorithm that can let us know a bird is flying over Peacetopia as accurately as possible.**
  **- We *want* the trained model to take no more than 10 sec to classify a new image.**
  **- We *want* the model to fit in 10MB of memory.**
  **Given models with different accuracies, runtimes, and memory sizes, how would you choose one?**
- [x] Find the subset of models that meet the runtime and memory criteria. Then, choose the highest accuracy.
- [ ] Create one metric by combining the three metrics and choose the best performing model.
- [ ] Take the model with the smallest runtime because that will provide the most overhead to increase accuracy.
- [ ] Accuracy is an optimizing metric, therefore the most accurate model is the best choice.


**3. Which of the following best answers why it is important to identify optimizing and satisficing metrics?**
- [ ] Knowing the metrics provides input for efficient project planning.
- [x] Identifying the metric types sets thresholds for satisficing metrics. This provides explicit evaluation criteria.
- [ ] Identifying the optimizing metric informs the team which models they should try first.
- [ ] It isn’t. All metrics must be met for the model to be acceptable.

**4. With 10,000,000 data points, what is the best option for train/dev/test splits?**
- [x] train - 95%, dev - 2.5%, test - 2.5%
- [ ] train - 60%, dev - 30%, test - 10%
- [ ] train - 33.3%, dev - 33.3%, test - 33.3%
- [ ] train - 60%, dev - 10%, test - 30%

**5. After setting up your train/dev/test sets, the City Council comes across another 1,000,000 images, called the “citizens’ data”. Apparently the citizens of Peacetopia are so scared of birds that they volunteered to take pictures of the sky and label them, thus contributing these additional 1,000,000 images. These images are different from the distribution of images the City Council had originally given you, but you think it could help your algorithm.**

**Notice that adding this additional data to the training set will make the distribution of the training set different from the distributions of the dev and test sets.**

**Is the following statement true or false?**

**"You should not add the citizens' data to the training set, because if the training distribution is different from the dev and test sets, then this will not allow the model to perform well on the test set."**

- [ ] True
- [x] False

Note: False is correct: Sometimes we'll need to train the model on the data that is available, and its distribution may not be the same as the data that will occur in production. Also, adding training data that differs from the dev set may still help the model improve performance on the dev set. What matters is that the dev and test set have the same distribution.

**6. One member of the City Council knows a little about machine learning, and thinks you should add the 1,000,000 citizens’ data images to the test set. You object because:**
- [x] The test set no longer reflects the distribution of data (security cameras) you most care about.
- [ ] A bigger test set will slow down the speed of iterating because of the computational expense of evaluating models on the test set.
- [x] This would cause the dev and test set distributions to become different. This is a bad idea because you’re not aiming where you want to hit.
- [ ] The 1,000,000 citizens’ data images do not have a consistent x-->y mapping as the rest of the data.

**7. You train a system, and its errors are as follows (error = 100%-Accuracy):**


|Training set error|Dev set error|
|---|---|
|4.0%|4.5%|


**This suggests that one good avenue for improving performance is to train a bigger network so as to drive down the 4.0% training error. Do you agree?**
- [x] No, because there is insufficient information to tell.
- [ ] Yes, because this shows your bias is higher than your variance.
- [ ] No, because this shows your variance is higher than your bias.
- [ ] Yes, because having a 4.0% training error shows you have a high bias.

**8. You want to define what human-level performance is to the city council. Which of the following is the best answer?**
- [ ] The average of regular citizens of Peacetopia (1.2%).
- [ ] The average of all the numbers above (0.66%).
- [x] The performance of their best ornithologist (0.3%).
- [ ] The average performance of all their ornithologists (0.5%)


**9. Which of the below shows the optimal order of accuracy from worst to best?**
- [ ] The learning algorithm’s performance -> Bayes error -> human-level performance.
- [x] Human-level performance -> the learning algorithm’s performance -> Bayes error.
- [ ] Human-level performance -> Bayes error -> the learning algorithm’s performance.
- [ ] The learning algorithm’s performance -> human-level performance -> Bayes error.

**10. After working on your algorithm you have to decide the next steps. Currently, human-level performance is 0.1%, training is at 2.0% and the dev set is at 2.1%. Which statement below best describes your thought process?**
- [x] Decrease regularization to boost smaller signals.
  *Note: Yes. Bias is higher than variance.*
- [ ] Get a bigger training set to reduce variance.
- [ ] Decrease variance via regularization so training and dev sets have similar performance.
- [x] Address bias first through a larger model to get closest to human level error.
  *Note: Yes. Selecting the largest difference from (train set error - human level error) and (dev set error - train set error) and reducing bias or variance accordingly is the most productive step.*

**11. After running your model with the test set you find it is a 7.0% error compared to a 2.1% error for the dev set and 2.0% for the training set. What can you conclude? (Choose all that apply)**
- [ ] Try decreasing regularization for better generalization with the dev set.
- [x] You should try to get a bigger dev set.
  *Note: Yes. The dev set performance versus the test set indicates it is overfitting.*
- [x] You have overfitted to the dev set.
  *Note: Yes. The dev set performance versus the test set indicates it is overfitting.*
- [ ] You have underfitted to the dev set.

**12. After working on this project for a year, you finally achieve: Human-level performance, 0.10%, Training set error, 0.05%, Dev set error, 0.05%. Which of the following are likely? (Check all that apply.)**
- [ ] This result is not possible since it should not be possible to surpass human-level performance.
- [x] The model has recognized emergent features that humans cannot. (Chess and Go for example)
  *Note: Yes. When Google beat the world Go champion, it was recognized that it was making deeper moves than humans.*
- [ ] There is still avoidable bias.
- [x] Pushing to even higher accuracy will be slow because you will not be able to easily identify sources of bias.
  *Note: Yes. Exceeding human performance means you are close to Bayes error.*

**13. It turns out Peacetopia has hired one of your competitors to build a system as well. You and your competitor both deliver systems with about the same running time and memory size. However, your system has higher accuracy! Still, when Peacetopia tries out both systems, they conclude they like your competitor’s system better because, even though you have higher overall accuracy, you have more false negatives (failing to raise an alarm when a bird is in the air). What should you do?**
- [ ] Pick false negative rate as the new metric, and use this new metric to drive all further development.
- [ ] Apply regularization to minimize the false negative rate.
- [ ] Ask your team to take into account both accuracy and false negative rate during development.
- [x] Brainstorm with your team to refine the optimizing metric to include false negatives as they further develop the model.

**14. You’ve handily beaten your competitor, and your system is now deployed in Peacetopia and is protecting the citizens from birds! But over the last few months, a new species of bird has been slowly migrating into the area, so the performance of your system slowly degrades because your model is being tested on a new type of data. There are only 1,000 images of the new species. The city expects a better system from you within the next 3 months. Which of these should you do first**
- [x] Augment your data to increase the images of the new bird.
- [ ] Add hidden layers to further refine feature development.
- [ ] Put them into the dev set to evaluate the bias and re-tune.
- [ ] Add the new images and split them among train/dev/test.

**15. The City Council thinks that having more Cats in the city would help scare off birds. They are so happy with your work on the Bird detector that they also hire you to build a Cat detector. (Wow Cat detectors are just incredibly useful, aren’t they?) Because of years of working on Cat detectors, you have such a huge dataset of 100,000,000 cat images that training on this data takes about two weeks. Which of the statements do you agree with? (Check all that agree.)**
- [x] Buying faster computers could speed up your teams’ iteration speed and thus your team’s productivity.
- [x] If 100,000,000 examples is enough to build a good enough Cat detector, you might be better off training with just 10,000,000 examples to gain a ≈10x improvement in how quickly you can run experiments, even if each model performs a bit worse because it’s trained on less data.
- [ ] Having built a good Bird detector, you should be able to take the same model and hyperparameters and just apply it to the Cat dataset, so there is no need to iterate.
- [x] Needing two weeks to train will limit the speed at which you can iterate.

---

**1. You meet with them and ask for just one evaluation metric. True/False?**
- [x] False
- [ ] True

**2. The city asks for your help in further defining the criteria for accuracy, runtime, and memory. How would you suggest they identify the criteria?**
- [x] Suggest to them that they define which criterion is most important. Then, set thresholds for the other two.
- [ ] Suggest to them that they focus on whichever criterion is important and then eliminate the other two.
- [ ] Suggest that they purchase more infrastructure to ensure the model runs quickly and accurately.

**3. The essential difference between an optimizing metric and satisficing metrics is the priority assigned by the stakeholders. True/False?**
- [ ] True
- [x] False

**4. Structuring your data. Before implementing your algorithm, you need to split your data into train/dev/test sets. Which of these do you think is the best choice**
- [ ] <table><tr><th>Train</th><th>Dev</th><th>Test</th></tr><tr><td>6,000,000</td><td>3,000,000</td><td>1,000,000</td></table>
- [ ] <table><tr><th>Train</th><th>Dev</th><th>Test</th></tr><tr><td>3,333,334</td><td>3,333,334</td><td>3,333,334</td></table>
- [x] <table><tr><th>Train</th><th>Dev</th><th>Test</th></tr><tr><td>9,500,000</td><td>250,000</td><td>250,000</td></table>
- [ ] <table><tr><th>Train</th><th>Dev</th><th>Test</th></tr><tr><td>6,000,000</td><td>1,000,000</td><td>3,000,000</td></table>

**6. One member of the City Council knows a little about machine learning and thinks you should add the 1,000,000 citizens’ data images proportionately to the train/dev/test sets. You object because:**
- [ ] The 1,000,000 citizens’ data images do not have a consistent x-->y mapping as the rest of the data.
- [x] The additional data would significantly slow down training time.
- [ ] The training set will not be as accurate because of the different distributions.
- [ ] If we add the images to the test set then it won't reflect the distribution of data expected in production.

**8. If your goal is to have “human-level performance” be a proxy (or estimate) for Bayes error, how would you define “human-level performance”?**
- [ ] The performance of the head of the City Council.
- [ ] The performance of their volunteer amateur ornithologists.
- [ ] The performance of the average citizen of Peacetopia.
- [x] The best performance of a specialist (ornithologist) or possibly a group of specialists.

**9. Which of the following statements do you agree with?**
- [ ] A learning algorithm’s performance can be better than human-level performance and better than Bayes error.
- [ ] A learning algorithm’s performance can never be better than human-level performance but it can be better than Bayes error.
- [ ] A learning algorithm’s performance can never be better than human-level performance nor better than Bayes error.
- [x] A learning algorithm’s performance can be better than human-level performance but it can never be better than Bayes error.

**10. Which of the following best expresses how to evaluate the next steps in your project when your results for human-level performance, train, and dev set error are 0.1%, 2.0%, and 2.1% respectively?**
- [ ] Port the code to the target devices to evaluate if your model meets or exceeds the satisficing metrics.
- [ ] Evaluate the test set to determine the magnitude of the variance.
- [x] Based on differences between the three levels of performance, prioritize actions to decrease bias and iterate.
- [ ] Keep tuning until the train set accuracy is equal to human-level performance because it is the optimizing metric.

**11. After running your model with the test set you find it is a 7.0% error compared to a 2.1% error for the dev set and 2.0% for the training set. What can you conclude? (Choose all that apply)**
- [ ] Try decreasing regularization for better generalization with the dev set.
- [x] You should try to get a bigger dev set.
- [x] You have overfitted to the dev set.
  *Note: Yes. The dev set performance versus the test set indicates it is overfitting.*
- [x] You have underfitted to the dev set.

**12. After working on this project for a year, you finally achieve:**

|Human-level performance|Training set error|Dev set error|
|--|--|--|
|0.10%|0.05%|0.05%|

**What can you conclude? (Check all that apply.)**
- [x] It is now harder to measure avoidable bias, thus progress will be slower going forward.
- [ ] With only 0.05% further progress to make, you should quickly be able to close the remaining gap to 0%
- [x] If the test set is big enough for the 0.05% error estimate to be accurate, this implies Bayes error is ≤0.05
- [ ] This is a statistical anomaly (or must be the result of statistical noise) since it should not be possible to surpass human-level performance.

**13. Your system is now very accurate but has a higher false negative rate than the City Council of Peacetopia would like. What is your best next step?**
- [ ] Look at all the models you’ve developed during the development process and find the one with the lowest false negative error rate.
- [ ] Reset your “target” (metric) for the team and tune to it.
- [x] Expand your model size to account for more corner cases.
- [ ] Pick false negative rate as the new metric, and use this new metric to drive all further development.

**14. You’ve handily beaten your competitor, and your system is now deployed in Peacetopia and is protecting the citizens from birds! But over the last few months, a new species of bird has been slowly migrating into the area, so the performance of your system slowly degrades because your model is being tested on a new type of data. There are only 1,000 images of the new species. The city expects a better system from you within the next 3 months. Which of these should you do first?**
- [ ] Add hidden layers to further refine feature development.
- [ ] Add the new images and split them among train/dev/test.
- [ ] Put them into the dev set to evaluate the bias and re-tune.
- [x] Augment your data to increase the images of the new bird.

---

**7. Human performance for identifying birds is < 1%, training set error is 5.2% and dev set error is 7.3%. Which of the options below is the best next step?**
- [x] Train a bigger network to drive down the >4.0% training error.
- [ ] Validate the human data set with a sample of your data to ensure the images are of sufficient quality.
- [ ] Try an ensemble model to reduce bias and variance.
- [ ] Get more data or apply regularization to reduce variance.

**8. You ask a few people to label the dataset so as to find out what is human-level performance. You find the following levels of accuracy:**
|||
|--|--|
|Bird watching expert #1|0.3% error|
|Bird watching expert #2|0.5% error|
|Normal person #1 (not a bird watching expert)|1.0% error|
|Normal person #2 (not a bird watching expert)|1.2% error|

**If your goal is to have “human-level performance” be a proxy (or estimate) for Bayes error, how would you define “human-level performance”?**
- [ ] 0.0% (because it is impossible to do better than this)
- [x] 0.3% (accuracy of expert #1)
- [ ] 0.4% (average of 0.3 and 0.5)
- [ ] 0.75% (average of all four numbers above)

**10. You find that a team of ornithologists debating and discussing an image gets an even better 0.1% performance, so you define that as “human-level performance.” After working further on your algorithm, you end up with the following:**
|||
|--|--|
|Human-level Performance|0.1% error|
|Training set error|2% error|
|Dev set error|2.1%|

**Based on the evidence you have, which two of the following four options seem the most promising to try? (Check two options.)**
- [x] Train a bigger model to try to do better on the training set.
- [ ] Try increasing regularization.
- [ ] Get a bigger training set to reduce variance.
- [x] Try decreasing regularization.

**11. After running your model with the test set you find it is a 7.0% error compared to a 2.1% error for the dev set and 2.0% for the training set. What can you conclude? (Choose all that apply)**
- [x] You have overfitted to the dev set.
  *Note: Yes. The dev set performance versus the test set indicates it is overfitting.*
- [x] You should try to get a bigger dev set.
  *Note: Yes. The dev set performance versus the test set indicates it is overfitting.*
- [ ] You have underfitted to the dev set.
- [ ] Try decreasing regularization for better generalization with the dev set.

**11. After working on this project for a year, you finally achieve:**
|||
|--|--|
|Human-level Performance|0.1% error|
|Training set error|0.05% error|
|Dev set error|0.05%|

**What can you conclude?**

- [x] It is now harder to measure avoidable bias, thus progress will be slower going forward.
- [ ] This is a statistical anomaly (or must be the result of statistical noise) since it should not be possible to surpass human-level performance.
- [x] With only 0.05% further progress to make, you should quickly be able to close the remaining gap to 0%
- [ ] If the test set is big enough for the 0.05% error estimate to be accurate, this implies Bayes error is ≤0.05

**13. It turns out Peacetopia has hired one of your competitors to build a system as well. Your system and your competitor both deliver systems with about the same running time and memory size. However, your system has higher accuracy! However, when Peacetopia tries out your and your competitor’s systems, they conclude they actually like your competitor’s system better, because even though you have higher overall accuracy, you have more false negatives (failing to raise an alarm when a bird is in the air). What should you do**
- [ ] Look at all the models you’ve developed during the development process and find the one with the lowest false negative error rate.
- [ ] Rethink the appropriate metric for this task, and ask your team to tune to the new metric.
- [x] Ask your team to take into account both accuracy and false negative rate during development.
- [ ] Pick false negative rate as the new metric, and use this new metric to drive all further development.

**14. You’ve handily beaten your competitor, and your system is now deployed in Peacetopia and is protecting the citizens from birds! But over the last few months, a new species of bird has been slowly migrating into the area, so the performance of your system slowly degrades because your data is being tested on a new type of data. You have only 1,000 images of the new species of bird. The city expects a better system from you within the next 3 months. Which of these should you do first?**
- [ ] Try data augmentation/data synthesis to get more images of the new type of bird.
- [ ] Put the 1,000 images into the training set so as to try to do better on these birds.
- [x] Add the 1,000 images into your dataset and reshuffle into a new train/dev/test split.
- [ ] Use the data you have to define a new evaluation metric (using a new dev/test set) taking into account the new species, and use that to drive further progress for your team.
  