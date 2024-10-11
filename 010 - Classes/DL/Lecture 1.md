What is AI?

Input x => program $(x, \theta)$ => output $\omega$
- $\theta$ is our parameters, which decide how good our model will be. 
- Classical algorithms have manually implemented rules
	- Other option is to use ML, which uses data (examples) in the form of pairs of inputs and sometimes outputs and let the model 'learn' by identifiying patterns. 
	- Traditionally ML require feature engineering, where the programmer has to decide which features are important for the predictions, and the performance will rely on how important those features really are for solving the problem.
	- DL is ML that uses neural networks with multiple layers, that automatically learn which features are important, it thrives on large datasets, the more data it has, the better it performs. 
	- Input layer takes the input $x$, output layer gives $\omega$, the hidden layers tune the parameters themselves. 
	- Chatgpt is a massive neural network

Initially 1 hidden layer, were okish, not very special. Later more data, bigger models. Worked much better in practice. 

## vectorial data
not structured data (rows in a table, no relationships with the datapoints)
For example iris dataset, classification. This is not strucutered data

Structured data:
data that has an inherent organization or relationships that is not very clear initially. Like a sequence of tokens, images, trees etc. The relationship between data is not directly clear. Does not easily fit in a table row and collumn. 

Relationship between pixels (not clear in vectors)

Time series 

For example:
- Alpha fold (input sequence of amino acids), output: 3d protein structure
- Chatgpt, using transformers. sequence of tokens as input and output. 
- Speech and language processing
- Self dirivng cars


Heavy use of uncertainty and probabilities in ML
We have inputs and outputs, and want to make predictions for new inputs. We want to show how sure we are about the output, so rather return an probability distribution. Even with a huge dataset we cannot account for every situation

Using probability for predictions avoids these problems:

Instead of a single prediction, we can return a range of possibilities
- probabilities help us measure how confident we are in our predictions 
- Probailities can be sued for optimal deciscion making

So our output $\omega$ will become a probability distribution instead of a single output. 

Loss function is a way to measure how good or bad the predictions of ML method are compared to the actual values in the data
- squared error
- 0-1

