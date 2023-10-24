20230823

Discover the potential information leakage, which is node features being contaminated by the bond information, like how much the bond has been connected to the specific node, etc. However, for inference, this information cannot be obtained. There are two possible ways to handle this problem. The first is to process partial molecules on the fly, while another approach is masking the bond information. Currently, I have decided on the second approach. 

20230824 

Plan: Tackling atom and fragment circumstances for the BFS masker, and making the train be passed. 

The model has been developed successfully, at least on the current molecules. However, each component should be checked carefully, with the specific debug mode. Today's assignment is finished! Tomorrow code the dataloader, and try to train on the dataloader successfully. 

20230825

The batching of data has been studied. It could be effectively approached under the PyG framework. Furthermore, it unifyies the shape of data for batching. For instance, attach_site should be that of shape 1,3 instead of shape 3. Besides, each sub-model has been adjusted to the batch training. 

20230826

Plan: Construct the dataloader and train on the dataloader successfully. 

Writing the get_loss function, write the lmdb file creating script

20230827

Write the Dataset instance, and write the training and evaluation pipeline. Then process data successfully and train the first version. However, the gradient tends to explode after the initial convergence. There are two hypotheses, one is that the stacked layer causes instability; the other is the unclear features confuse the model. 

20230828

Plan: Change the feature parsing in the morning, and test it again. In the afternoon, try to split the other two heads from the classification part. 

20230829 

Confronting the gradient explosion problem again, even trying with loss clamping and gradient clipping. In the morning, I found out that double softmax operations may contribute to this problem. That is to say, the normalized operation has already been done inherently inside the torch.CrossEntropy(), afterward, operating softmax outside is detrimental to the numerical stability. Fixing this bug results in other types of losses successfully converging. However, next_attach_site loss doesn't work. I will try to consider symmetry as a judgment to mitigate this problem. Furthermore, I'm not sure whether the position would converge or if we need several circles to make it converge. 

20230830

Plan B: Chemical Consideration, incorporating bonding relationships prediction with one model. 
