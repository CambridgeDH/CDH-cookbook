# The Word in the Machine: An Applied Investigation of LLMs through the Lens of Philosophy of Language 
<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Methods Fellows 2025</a></p>

## Contents
- [Introduction](#introduction)
- [Operationalising Wittgenstein through ‘fill-mask’](operationalising-wittgenstein-through-fill-mask)
- [‘Cybernetic writing’ and the semantics of unidirectional LLMs](#cybernetic-writing-and-the-semantics-of-unidirectional-llms
- [References](#references)

Code Repository:
<https://github.com/alessandrocam/The-Word-in-the-Machine>.

## Introduction

The objective of this lesson is to offer both theoretical and practical
insights into how we might make sense of the language produced by large
language models (LLMs).

I would like to begin with a brief reflection on what motivates such an
investigation. After all, we are not ordinarily puzzled by the language
contained in a book, or transmitted by a television, or produced by
other media technologies. A text in a book is read, a broadcast is
followed or ignored, but the question of meaning is not directed toward
the book or the television as if they were themselves bearers of
linguistic understanding. And yet, this question seems to acquire a new
urgency in the context of the recent emergence of LLMs. We find
ourselves asking not only what these systems produce, but what their
outputs mean, as though interpretation were required at the level of the
system itself.

For the purposes of this lesson, I will simply note that one important
factor behind this shift is our strong tendency to anthropomorphise
chatbots. We readily ascribe to them capacities such as meaning,
understanding, thought, intention, and even creativity. This tendency is
not new. It was first observed by Joseph Weizenbaum in the 1960s in
response to users’ interactions with ELIZA, a comparatively rudimentary
chatbot that nevertheless elicited remarkably human-like attributions
from its users.[^1] If people were inclined to attribute understanding
to ELIZA, it is perhaps unsurprising that contemporary language models,
whose linguistic abilities are vastly more sophisticated, provoke such
responses even more strongly. As Murray Shanahan has observed:

> ‘LLM-based conversational agents blur the line between problematic and
> unproblematic cases of anthropomorphism. For example, I might remark
> that “the thermostat thinks it’s too cold in here” without the word
> “thinks” entailing the expectation that I could go and have a
> conversation with the thermostat about the weather. By contrast, when
> I say that “ChatGPT thinks the current Wimbledon men’s champion is
> Carlos Alcaraz” this does come with the expectation that I could have
> a conversation with ChatGPT about tennis. Accordingly, the question of
> whether or not LLMs “really” have beliefs become a matter of
> philosophical debate.’[^2]

Despite our tendencies to anthropomorphise LLMs, however, it is
important to note that these models do not share the socio-linguistic
and physiological context that, as Wittgenstein argues, gives our
utterances meaning. To use Wittgenstein’s terminology, LLMs do not
participate in our ‘forms of life’.[^3] They do not engage in the
practices, activities, and modes of existence within which human
language acquires its significance. The challenge, then, is to
foreground this fundamental difference between human language and
LLM-generated text. Rather than asking whether language models possess
the same kinds of meanings that we do, the aim of this lesson is to
explore the distinctive—and perhaps alien—character of the meanings that
emerge from their operations. The broader philosophical question of
whether LLMs genuinely grasp, constitute, or instantiate meaning at all
lies beyond the scope of this discussion and is best reserved for more
detailed treatment elsewhere.

This lesson thus explores how language operates within LLMs through a
series of simple but revealing experiments. The code used throughout
these experiments is available in the GitHub repository
<https://github.com/alessandrocam/The-Word-in-the-Machine>. Beyond
reproducing the rather mundane examples discussed here, the repository
is intended as a toolkit for further philosophical investigation into
the exotic mechanics of LLM-language, particularly with the method
of ‘cybernetic writing’ introduced in the final section of the lesson.

## Operationalising Wittgenstein through ‘fill-mask’

To bring out the exotic character of LLM-generated language, I adopt a
method of inquiry that Wittgenstein identifies for investigating the
meaning of a word. The point is not to ask what a word means for an LLM,
but to examine what happens when we pursue this inquiry in the case of
LLM-generated language, and thereby to reveal the ways in which it
differs from human language. Namely, for Wittgenstein, the meaning of a
word in a sentence can be discovered and surveyed by analysing the other
words it can be replaced by. This is the example he gives in *PI* §558:

> ‘What does it mean to say that the “is” in “The rose is red” has a
> different meaning from the “is” in “Two times two is four”? \[…\]
> \[T\]he rule which shows that the word “is” has different meanings in
> these sentences is the one allowing us to replace the word “is” in the
> second sentence by the sign of equality, and forbidding this
> substitution in the first sentence’.

In my experiments, I use LLMs to visualise Wittgenstein’s intuition and
operate a kind of automated word substitution. Specifically, to obtain
the results that I will be discussing shortly, I used RoBERTa, a
bi-directional encoder-only LLM derived from the seminal BERT
architecture developed at Google.[^4] The technique implemented is
called ‘fill-mask’. It involves replacing a token in a sentence with a
special masked token and asking the model to predict which token is most
likely to occupy that position given the surrounding context.
Importantly, a token is not necessarily equivalent to a word: depending
on the model's tokenisation scheme, it may correspond to a whole word,
part of a word, punctuation mark, or another sub-word unit.

It is important to note that this experiment is not an exact
implementation of the substitution procedure proposed by Wittgenstein.
An LLM does not literally substitute one word for another; rather, it
predicts a token that is likely to occupy a particular position in a
sequence. This distinction is more than a technical detail.
Wittgenstein's method presupposes the ability to identify a word's
meaning and to replace it with another expression that performs a
similar function. Token prediction, by contrast, operates differently.
The model does not search for synonyms or attempt to preserve meaning as
such. Instead, it generates a probability distribution over possible
continuations on the basis of patterns learned from linguistic data. The
resulting substitutions may overlap with what a human reader would
regard as semantically similar alternatives, but this similarity emerges
as a consequence of prediction rather than as its goal. This observation
raises a broader question about the nature of linguistic competence.
What does it mean to substitute a word—to grasp its meaning and identify
the closest alternative expression? If this ability cannot be attributed
to an LLM, then what other capacities associated with meaning,
understanding, and interpretation might also require reconsideration?
Conversely, what new forms of linguistic behaviour become visible once
we begin to view language as a field of probabilistic expectations?

With this distinction in place, we can now examine the predictions
provided by RoBERTa for the word position corresponding to ‘is’ in the
two sentences from Wittgenstein’s example. The outcome of this
experiment is visualised in tables 1 and 2, data taken
from my Jupyter notebook. Wittgenstein's intuition is broadly confirmed.
For the masked token in the first sentence, the model predicts multiple
verbs associated with change or transformation, whereas, in the second
sentence, it recognizes the mathematical value of the token, predicting
terms such as ‘equals’, ‘=’, or ‘gives’.

The top ten predictions generated by RoBERTa for the masked token in the sentence "The rose &lt;mask&gt; red."

<table>
<caption>Table 1</caption>
<tr><td>is</td><td>0.3658</td></tr>
<tr><td>was</td><td>0.3602</td></tr>
<tr><td>turned</td><td>0.0740</td></tr>
<tr><td>turns</td><td>0.0341</td></tr>
<tr><td>became</td><td>0.0137</td></tr>
<tr><td>went</td><td>0.0115</td></tr>
<tr><td>gets</td><td>0.0103</td></tr>
<tr><td>goes</td><td>0.0092</td></tr>
<tr><td>becomes</td><td>0.0064</td></tr>
<tr><td>got</td><td>0.0049</td></tr>
</table>

Table 2 shows the top ten predictions generated by RoBERTa for the masked token in the sentence "Two times two &lt;mask&gt; four."

<table>
<caption>Table 2</caption>
<tr><td>equals</td><td>0.4111</td></tr>
<tr><td>is</td><td>0.1975</td></tr>
<tr><td>makes</td><td>0.1458</td></tr>
<tr><td>times</td><td>0.1257</td></tr>
<tr><td>=</td><td>0.0294</td></tr>
<tr><td>becomes</td><td>0.0179</td></tr>
<tr><td>means</td><td>0.0157</td></tr>
<tr><td>equal</td><td>0.0139</td></tr>
<tr><td>gets</td><td>0.0058</td></tr>
<tr><td>gives</td><td>0.0056</td></tr>
</table>

Moving beyond Wittgenstein's observations, how should we interpret these
lists of predictions for the two occurrences of the masked token? What
features ought we to attend to? We immediately notice from these
predictions that the semantic relations captured by the model reveal
much more than the possible logical function of ‘is’ discerned by
Wittgenstein. In Table 1, there are past tense forms of verbs, often
more probable than the corresponding present tense. In Table 2, one of
the words predicted by the model would render the sentence
ungrammatical, ‘Two times two *equal* four’. There are predictions which
give rise to somewhat unidiomatic sentences: e.g. ‘The rose *went/got*
red’. What dynamic of linguistic production is at play here?

It is important to recognise that the explanation for why the model
chose any one of these words must be sought exclusively within the
structure and content of the sentence itself. It is in relation to a
particular configuration of language that the model infers a context of
use—a form of life, one might say—and thereby a language-game within
which the masked token is to be predicted. The semantic choices of an
LLM can therefore only be understood against the background of the
linguistic environment from which they emerge. In this respect, meaning
is not determined by any direct engagement with the world, but by the
relations that obtain among linguistic forms: the textual patterns
present in the model’s training data that are reproduced in the
linguistic input provided by the user.

It thus follows that even slight alterations of an input sequence—of its
syntactic structure, or of its lexicon—can produce a dramatic shift in
the model’s output, as if it were produced as part of a different form
of life. Consider, for instance, in Table 3, the predictions generated
by RoBERTa for the masked token in the following sentence, which differs
from the first one only in the interposition of the phrase "in my opinion": "The rose, in my opinion, &lt;mask&gt; red."

<table>
<caption>Table 3</caption>
<tr><td>is</td><td>0.7261</td></tr>
<tr><td>was</td><td>0.1258</td></tr>
<tr><td>looks</td><td>0.0171</td></tr>
<tr><td>smells</td><td>0.0169</td></tr>
<tr><td>runs</td><td>0.0096</td></tr>
<tr><td>turns</td><td>0.0089</td></tr>
<tr><td>turned</td><td>0.0075</td></tr>
<tr><td>goes</td><td>0.0063</td></tr>
<tr><td>means</td><td>0.0045</td></tr>
<tr><td>went</td><td>0.0036</td></tr>
</table>

Here, I wish to emphasise that seven of the top ten predictions are
present-tense verbs (with ‘is’ now substantially more ‘likely’ than
‘was’), which conveys a more tentative, descriptive tone, rooted in the
transient ‘now’ to which sensory perception is confined. Pursuing this
line of interpretation, I would like to draw attention to the new words
predicted by RoBERTa: namely, these are verbs related to subjective,
sensory experience such as ‘looks’ and ‘smells’. In the case of the
latter prediction— ‘smells’— we are reminded that the LLM does not
participate in our forms of life, producing a statement that humans
would hardly ever utter, which we might even regard as nonsensical.
Crucially, however, this sentence *in potentia* is not due to a
malfunction of the model. Rather, it serves as a useful reminder that
LLMs are not trained to communicate propositions and do not operate on
the basis of truth conditions. Instead, they capture patterns of
co-occurrence—and, consequently, semantic similarity—between the tokens
they are trained on. We might reasonably doubt that RoBERTa's training
data contained any instances of a rose being described as *smelling
red*. Nonetheless, the insertion of the phrase ‘in my opinion’ signals
that ‘smells’* *belongs to the same region of the model’s learned
semantic space as the sensory predicates* *of sight. A similar point
goes for predictions which would render a sentence ungrammatical: they
are not *wrong* for the model in any straightforward sense, rather
(generally) less probable than the correct alternatives.

What emerges from these preliminary experiments is that LLMs demand a
fundamentally new way of reading in order to interpret their outputs.
This new way of reading is founded *not* in propositional logic or in
referential theories of semantics. Instead, we are to read the discrete
meanings of the predicted tokens as collectively enacting a pattern of
linguistic use and, thus, as simulating a social context. Because of
this, I posit that the outputs of LLMs are best read as distributions of
tokens, rather than as clean assertions formed by only the most likely
predictions to the exclusion of all the others, as they are often
presented in the ‘chat’ interfaces we have become familiar with. These
token distributions are then to be interpreted as a *gestalt*, I argue,
the meaning of each token to be aggregated with the others into a whole
that is more than the sum of its parts.

## ‘Cybernetic writing’ and the semantics of unidirectional LLMs

I would like to conclude this lesson with a brief note on how we might
investigate meaning in contemporary LLMs. Much of the methodology
discussed so far has been developed with bidirectional models in mind.
However, bidirectional language models such as RoBERTa are no longer at
the forefront of research and have largely been superseded by
unidirectional, autoregressive models. It is therefore worth considering
how a similar approach might be adapted to systems such as ChatGPT,
Gemini, or Claude.[^5] Unlike bidirectional models, which can draw on
context both before and after a given token, unidirectional models
process text in a single direction, from left to right. As a
consequence, we cannot investigate meaning by masking a token and
examining the predictions licensed by the surrounding context on both
sides.

To address this limitation of unidirectional LLMs, I propose a slightly
revised methodology. Let us consider two sentences, *a* and *b*. Rather
than varying a masked token within a fixed sentence, we iteratively
modify sentence *a*—by rephrasing it, substituting words, altering its
context, and so on—and then observe how these changes affect the
probability that the model assigns to proposition *b* as a continuation.
In other words, we investigate the conditions under which the model is
more or less likely to produce *b*. I choose to vary *a* rather than *b*
because the probabilities assigned to alternative continuations are
sensitive to their length. Longer strings tend to appear less likely
simply because their cumulative log likelihood is distributed across a
greater number of tokens, which would make differences in probability
difficult to interpret. Conversely, the length of *a*—within the model’s
maximum context window—does not systematically affect the probability
that *b* will follow.

Now, suppose we wish to investigate how pain utterances are represented
in a unidirectional LLM. Rather than asking which words can replace
‘pain’, or related terms, in a sentence, we examine which preceding
prompts make the model most likely to continue with expressions of pain
and, conversely, what subsequent generations such utterances license. By
way of example, let us suppose that we are interested in the expression
‘it hurts’. By exploring the range of prompts that increase or decrease
the probability of this utterance, we begin to gain an intuition for the
role it plays within the model’s linguistic practice. We might compare
descriptions of physical injury, emotional distress, requests for help,
medical consultations, and other contexts, and observe how strongly each
tends to elicit the target utterance. We might also inquire whether the
expression is typically uttered in the first or third person and, if in
the first person, what sort of speaker is most likely to produce it, and
how their voice can be rendered in text. Investigating the likelihood of
an utterance in an LLM therefore requires a considerable degree of
narrative imagination. Thus, starting from a prompt such as ‘I have lost
my job and’, we can discover that, when uttered by a middle-aged man,
from a complicated family background, addressing an interlocutor or
audience, this expression becomes even more likely to lead to ‘it
hurts’ than many prompts describing situations of physical injury.

From this methodology emerges a practice of writing with LLMs that I
term ‘cybernetic writing’. An LLM is, fundamentally, a cybernetic
system. In the absence of participation in a human form of life, it
acquires its linguistic competence through processes of feedback and
correction, adjusting its parameters in relation to the vast corpus of
texts on which it is trained. Its production of language is therefore
governed not by understanding in any ordinary sense, but by a history of
iterative optimisation. I am interested in what follows when writing
itself is conceived through this cybernetic framework. If the model is a
cybernetic system, what role do we occupy when we write with it? How do
our interventions become incorporated into the loops of prediction,
correction, and control that govern its outputs?

This question becomes particularly salient in the practice commonly
referred to as ‘prompt engineering’. Here, the writer's task is not
simply to express a thought but to formulate an input that will elicit a
desired continuation. Writing becomes an exercise in steering a
probabilistic process. To explore this phenomenon, I draw upon the
concept of ‘feedforward’. Long before the term was appropriated by
contemporary machine learning, it was introduced by the literary critic
I. A. Richards.[^6] He used ‘feedforward’ to describe a communicative
process in which a speaker or writer anticipates the effects their words
will have on an audience and adjusts their language accordingly.
Communication, on this account, depends not merely on feedback received
after an utterance but on the prior projection of possible responses.
This concept provides a useful lens through which to understand writing
with LLMs. Prompting a model involves constructing a text *a* in
anticipation of a subsequent text *b*. This is particularly relevant in
a philosophical investigation of concepts learned by an LLM, such as the
concept of pain, since such an investigation requires identifying the
linguistic conditions under which particular expressions become likely
to occur. The writer iteratively modifies the prompt, observes the
resulting output, and revises the prompt again, seeking to increase (or
decrease) the probability that a specific continuation will emerge.
Cybernetic writing is thus a collaborative yet asymmetrical process in
which the human writer learns to orient their language toward the
predictive dynamics of the machine.

The thought with which I would like to conclude this lesson is that
perhaps ‘read’ is not the most appropriate verb for what we do when
interpreting the output of LLMs—or, at the very least, it names a
practice that differs radically from reading human-authored language. To
engage with LLM outputs is not primarily to treat them as assertions of
propositions, but to reconstruct the social contexts that the model has
learned to simulate. In this sense, interpretation is inseparable from
writing with the model: we probe its meanings by prompting, steering,
and responding, rather than by passively decoding finished text. Writing
is instrumental to interpretation, it sets the ground for it and
proceeds from it, in a cybernetic loop that mirrors the modality by
which these models are trained.

## References

Devlin, Jacob, and others, ‘BERT: Pre-training of Deep Bidirectional
Transformers for Language Understanding’, arXiv:1810.04805 \[cs.CL\],
2019, <https://arxiv.org/abs/1810.04805>

Grattafiori, Aaron, and others, ‘The Llama 3 Herd of Models’,
arXiv:2407.21783 \[cs.AI\], 2024, <https://arxiv.org/abs/2407.21783>

Liu, Yinhan, and others, ‘RoBERTa: A Robustly Optimized BERT Pretraining
Approach’, arXiv:1907.11692 \[cs.CL\],
2019, <https://arxiv.org/abs/1907.11692>

Richards, I. A., *Speculative Instruments (*London: Routledge & Paul,
1955)

Shanahan, Murray, ‘Simulacra as Conscious Exotica’, *Inquiry* (2024),
1-29, doi: 10.1080/0020174X.2024.2434860

Weizenbaum, Joseph, ‘ELIZA—A Computer Program for the Study of Natural
Language Communication between Men and Machines’, *Communications of the
ACM*, 9 (1966), 36–45

Wittgenstein, Ludwig, *Philosophical Investigations*, trans. by G. E. M.
Anscombe, P. M. S. Hacker, and Joachim Schulte, 4th rev. edn
(Chichester: Wiley-Blackwell, 2009)

[^1]: See Joseph Weizenbaum, ‘ELIZA—A Computer Program for the Study of
    Natural Language Communication between Men and
    Machines’, *Communications of the ACM*, 9 (1966), 36–45.

[^2]: Murray Shanahan, ‘Simulacra as Conscious Exotica’, *Inquiry*
    (2024), 1-29, doi: 10.1080/0020174X.2024.2434860.

[^3]: The expression ‘form of life’ occurs only seven times in
    Wittgenstein’s published writings. The most cited uses are those
    found in sections §§19, 23, 241, and §§PPF 1, 345 from Ludwig
    Wittgenstein, *Philosophical Investigations* (hereafter *PI*),
    trans. by G. E. M. Anscombe, P. M. S. Hacker, and Joachim Schulte,
    4th rev. edn (Chichester: Wiley-Blackwell, 2009). All further
    references are to this edition.

[^4]: Yinhan Liu and others, ‘RoBERTa: A Robustly Optimized BERT
    Pretraining Approach’, arXiv:1907.11692 \[cs.CL\],
    2019, <https://arxiv.org/abs/1907.11692> \[accessed 17 June 2026\];
    see also Jacob Devlin and others, ‘BERT: Pre-training of Deep
    Bidirectional Transformers for Language Understanding’,
    arXiv:1810.04805 \[cs.CL\],
    2019, <https://arxiv.org/abs/1810.04805> \[accessed 17 June 2026\].

[^5]: For the experiments reported in the GitHub repository linked
    above, I used LLaMa 3.2-1B, developed by Meta AI. For details on the
    LLaMa family of models see Aaron Grattafiori, and others, ‘The Llama
    3 Herd of Models’, arXiv:2407.21783 \[cs.AI\], 2024,
    <https://arxiv.org/abs/2407.21783> \[accessed 18 June 2026\].

[^6]: See I. A. Richards, *Speculative Instruments (*London: Routledge &
    Paul, 1955).


<p class="credits">Written by Alessandro Trevisan, 2026-06-18<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>
<p class="previous-next-lesson"><a href="toc.html">Methods Fellows 2025 lessons</a></p>

