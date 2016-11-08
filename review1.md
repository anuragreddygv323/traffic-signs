# Requires Changes

## 4 SPECIFICATIONS REQUIRE CHANGES

This is a really excellent submission with great performance. You've made a lot of well thought-out decisions like transforming images to augment the data and converting to YUV to use the Y luminance.

The parts that aren't meeting specifications are just about including more details in the report about your process and final results. For example, what exactly was your initial model, and what were the intermediate steps from getting from the initial model to the final model? What was the final model? How was performance on the test set compared to the 5 images chosen for the second part of the report?

One idea to keep in mind is to try not to force the reader to have to look at the code to understand what was done. For example, I could figure out the final architecture by reading through the code, but ideally the report will give the reader that information.
# Dataset Exploration

## Student performs a visualization on the dataset.
Great job exploring the data with a variety of visualizations.

Just one little note: The report was saying that the data set distribution was "skewed". Skewed usually refers to a continuous variable where there are either more values on the high end or low end. In this case, even though the image category is represented by a number, the variable is categorical. When there are more values of one category over another category, sometimes you'll see this being called "imbalanced data".

It can affect model performance and also how a model is evaluated. If the model is trained on imbalanced data, then the model will end up seeing many more of one type of sign over other types of signs. This could affect performance. Also, we can end up with a very "accurate" model even if it can't predict certain classes correctly. For examples, it looks like there are only about 200 images with label 0. What if we make a model that never predicts one of those images correctly? It will hardly affect accuracy since there were so few images labeled "0". But the model will always be wrong whenever it sees one of those signs.
# Design and Test a Model Architecture

## Student thoroughly discusses the approach taken for deriving and designing a model architecture fit for solving the problem given.
The report is giving a general idea about the approach that was taken. For example, I know that you've used some literature resources to come up with the general convolution network architecture. And the report gives a general sense for what the final architecture was:
```input_image -> one of several conv_block -> fully_connected_block -> output_logit.```

But the report isn't really documenting the details for how the final architecture was derived. In the report, please include the details of your iterative process. For example, what was the exact model and set of parameters you tried first? How were the results? What did you think could be improved and how did you improve it? What was the second architecture tried, and what were the results? What did you think could be improved, and what was done to improve the third version?

If you tried dozens or 100s of versions, it's not necessary to give the exact details of every small change. But please at least provides the major changes that were done between iterations and what was done to improve the architecture for the next round.

The report could discuss how other techniques were decided upon as well like if you used cross validation to see if color vs Y of YUV was providing better results. How were the filter sizes chosen for the convolution? Kernel sizes for max pooling? Probabilities for dropout?
Student provides sufficient details of the characteristics and qualities of the architecture, such as the type of model used, the number of layers, the size of each layer. Visualizations emphasizing particular qualities of the architecture are encouraged.
Make sure in question number 3 that the answer discusses the actual final model chosen. The answer is giving a general description of what the convolution neural network architecture looks like, but it's not actually giving the final model.

In other words, the answer here should say input layer -> convolution (depth = 64) -> RELU -> Dropout (prob = ?), etc. with the exact details of the final model. Although somebody could read through the code to figure this out, ideally the report stands on its own without somebody having to read through and understand all of the code. The description of the final architecture could also mention where padding and softmax were used.

There's no requirement to make a visualization, but visualizations of the final network are encouraged as well: https://en.wikipedia.org/wiki/File:Typical_cnn.png
## Students provides sufficient details of the preprocessing techniques used. Additionally, the student discusses why the techniques were chosen.
The report is clear about what preprocessing techniques were used (augmentation, train/cross-validation split, greyscale with YUV transformation, feature scaling, randomized initialization) and why they were used. Great job both scaling the data and using a greyscale transformation.

The report mentions a couple of times that the "V" channel of YUV was used to create greyscale images although that looks like a typo. The "Y"channel would be used for greyscale and it looks like from the code that the Y channel is being used.

Another technique that could be explicitly mentioned is one-hot encoding of the labels, but that would pretty much be implied when using a neural network.

I thought getting the baseline with nearest neighbors was a great idea. The report said that another baseline that could be used would be 1/43 if random guessing was being used. If all of the classes were equally represented, then the probability of a random guess being correct would be 1/43. But because of the imbalanced data, the probabilities would be slightly different. We could get an even higher baseline model by just saying all traffic signs are class 2 since that had the most samples. I'm just mentioning it since it relates to what I mentioned previously about imbalanced data.
## Student describes how the model was trained and evaluated. If the student generated additional data they discuss their reasoning.
### meets specifications

The submission describes how the data was split into training/cross-validation sets. It doesn't directly give the details about how cross-validation was used to find a final architecture, but I discussed that in a different part of the rubric already.

In terms of the additional data generated, the report discusses why additional data was generated. As part of the discussion of the final training strategy,

### required change

This is a really small required change. Just make sure that in the report, it's clearly stated how many extra images were added to each image in the data set as part of the augmentation. A reader could be able to figure out by reading through the code, but ideally, the report makes this clear so that the reader doesn't have to dive into the code to understand what was done.

### suggestion

As a suggestion, the number of extra images to output per data point could be weighted by the representation of the class in the data set. What I mean is that, for example, a class 0 image could be augmented more times than a class 1 image since there are very few class 0 images. That could help with the imbalanced classes. In the end, this might not matter much since you're already getting 100% training and cross validation accuracy.
# Test a Model on New Images

## Student chooses five candidate images of traffic signs taken and visualizes them in the report. Discussion is made as to any particular qualities of the images or traffic signs in the images that may be of interest, such as whether they would be difficult for the model to classify.
Great job looking at both images from your neighborhood as well as images found online. The report has a good discussion of any potential difficulties that might arise when classifying.
Student documents the performance of the model when tested on the captured images and compares it to the results of testing on the dataset.
This part of the report has a really interest analysis. You've chosen some challenging images, and the results are excellent.

To meet specifications, just also make sure to compare performance on the test set with the performance on these extra images. Here are some ideas of how they could be compared:

    - what was the accuracy for each individual sign type? For example, what was the accuracy for predicting stop signs on the test set? Is it higher or lower than the accuracies for other sign types? Does that help explain why the model might have mis-classified the first stop sign?
    - compare the top 5 softmax probabilities on the test set versus the new images. For example, what did the top 5 softmax probabilities tend to be on the training set for stop signs? Is that in agreement with the top 5 probabilities on these new images?
The softmax probabilities of the predictions on the captured images are visualized. The student discusses how certain or uncertain the model is of its predictions.
Great discussion of the softmax probabilities on the captured images.

Instead of putting the results in a table, consider maybe using a chart like a bar chart. Also, ideally this image would show the top 5 softmax probabilities instead of just the top 1:

Screen Shot 2016-11-07 at 1.51.34 PM.png