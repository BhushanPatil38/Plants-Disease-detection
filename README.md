# Plants-Disease-detection
###   
This is a combination of the Keras callbacks Reduce Learning Rate on Plateau,Early Stopping and Model Checkpoint but eliminates some of the limitations of each. It also provides a handy feature that enables you to set the number of epochs to train for until a message asks if you wish to halt training on the current epoch by entering H or to enter an integer which will determine how many more epochs to run before the message appears again. This is very useful if you are training a model and decide the metrics are satisfactory and you want to end the model training early. The callback always returns your model with the weights set to those of the epoch which had the highest performance on the metric being monitored (accuracy or validation accuracy) The callback initially monitors training accuracy and will adjust the learning rate based on that until the accuracy reaches a user specified threshold level. Once that level of training accuracy is achieved the callback switches  to monitoring validation loss and adjusts the learning rate based on that the callback is of the form:  

callbacks=[LRA(model, patience, stop_patience, threshold,factor, dwell,
               model_name, freeze, batches,initial_epoch, epochs, ask_epoch )]    
       
 ### ** Example:
 Callbacks=[LRA(my_model, 2, 5, .9, .5, True, 'InceptionResnetV2', False, 80,20,10)]
 This implies:
 
 - after 2 epochs of no improvement the learning rate will be reduced
 - after 5 consecutive adjustment of the leaarning rate with no metric improve training terminates
 - once the training accuracy reaches 90% the callback adjust learning rate based on validation loss
 - when the learning rate is adjust the new learning rate is .5 X learning rate
 - if the current epoch's metric value did not improve, the weights for the prior epoch are loaded
   and the learning rate is reduced
 - the string name of your model to print in the header at the start of training
 - the header will note the entire model is being trained
 - the number of batches per epoch is 80
 - train for 20 epochs
 - after the tenth epoch you will be asked if you want to halt training by entering H or enter 
   an integer denoting how many more epochs to run before you will be prompted again
                 
