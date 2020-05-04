# GuideBert

GuideBert is a method to pretrain Bert-like models. Given a textual input, GuideBert generates a masking pattern and later on tries to "unmask" it again. It uses one single Bert-like model with two heads:
1. a binary classification head to predict for each token if it should be masked, and
2. a language modeling head to (re-)generate the masked tokens.

End-to-end training is achieved by using a [Gumble-Softmax](https://arxiv.org/pdf/1611.01144.pdf) layer after the masking step and also inverting the gradients at this point.  

Currently, the mean proportion of tokens to mask (config parameter `p_mask_target`) is controlled by an additonal loss whose weight is defined by config parameter `lambda_mask_loss` (see defaults in the [config class](https://github.com/ArneBinder/transformers/blob/guidebert/src/transformers/configuration_guidebert.py)).

This repo holds only the config files and some backlog information. For the actual code, see [the guidebert branch of huggingface/transformers](https://github.com/ArneBinder/transformers/blob/guidebert/src/transformers/modeling_guidebert.py).
