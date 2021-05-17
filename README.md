# Restricted-Boltzmann-Machines
__UCI CS179__

Restricted Boltzmann machines are undirected models for binary-valued data X that use one or more layers of binary-valued latent variables Z to create complex distributions.  When many layers are used, they are sometimes called Deep Boltzmann Machines (see for example [this demo](http://npcontemplation.blogspot.com/2012/02/machine-that-can-dream.html), or [this one](http://www.cs.toronto.edu/~hinton/digits.html))

One possibility is to apply an RBM-based model to the recommender system (MovieLens) data, binarized to represent "like / dislike" information.  If we treat each user (row) as a sample from some distribution p(X), we can learn a p(X) that uses binary latent categories Z to explain why certain movies are "liked" or "disliked" together.  To use such a model for recommendations, we would learn p(X), then for any new user, take the *known* likes and dislikes, condition the model on them, and then infer the distribution of the remaining items. (Which item has the highest probability of being liked?  Which items are we most confident of?)  More advanced uses of the model might use ideas from active learning to propose items for the user to rate, so that we would more quickly resolve their latent interests and thus make better recommendations.

Other ideas to explore:  

  - How does the complexity of the model (number of latent variables) affect the result quality?  Can you do model selection to determine which model is the best? 
  - If you use or write an implementation that allows more than two layers ("deep"), how do depth and layer width (nodes per layer) interact to determine quality? 
  - Conditional RBMs include extra information that will always be known, so that we model p(X,Z | K) using an RBM.  These models can be used for denoising images (K=noisy image, X=original image), or to add side information (K=demographic or other user info, X=user ratings of movies). 
  - You could compare different methods of training.  Most RBMs train using an MCMC-based estimate of the maximum likelihood derivative (called "persistent contrastive divergence" in the RBM literature), but can also be trained using CD or loopy BP.
