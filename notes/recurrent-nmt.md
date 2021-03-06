## [Recurrent Neural Machine Translation](http://arxiv.org/abs/1607.08725)

TLDR; The authors replace the standard attention mechanism (Bahdanau et al) with a RNN/GRU, hoping to model historical dependencies for translation and mitigating the "coverage problem". The authors evaluate their model on Chinese-English translation where they beat Moses (SMT) and GroundHog baselines. The authors also visualize the attention RNN and show that the activations make intuitive sense.

#### Key Points

- Training time: 2 weeks on Titan X, 300 batches per hour, 2.9M language pairs

#### Notes

- The authors argue that their attention mechanism works better b/c it can capture dependencies among the source states. I'm not convinced by this argument. These states already capture dependencies because they are generated by a bidirectional RNN.
- Training seems *very* slow for only 2.9M pairs. I wonder if this model is prohibitively expensive for any production system.
- I wonder if we can use RL to "cover" phrases in the source sentences out of order. At each step we pick a span to cover before generating the next token in the target sequence.
- The authors don't evaluate Moses for long sentences, why?