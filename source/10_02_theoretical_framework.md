# Marco Teórico

This section is intended to be a starting point for the reader, so that she can understand the fundamental ideas and the underlying concepts of the work presented in this thesis.
It is separated in three sections, each one with a different purpose. 
First, we describe broadly MDE and its role in the development of software. Second, we describe the use of NLP and language models (LM) to extract usable text embeddings out of software models. Third, we describe the  transformer architecture, a deep learning model state of the art in language modelling, able to extract usable embeddings from text corpora.

## Model Driven Engineering


### Language Models

Models that assign probabilities to sequences of words are called language models or LMs. Given a sequence of tokens, they are usually trained to compute the probability of the sequence given its history, i.e. the next word in a sequence of words [@language_models_sentences].
They attempt to model understanding of a domain language in a corpus of text, and sometimes they can act as a knowledge base. LMs enable applications such as text summarization, text classification, and information retrieval among many others.

Language modeling is usually framed as unsupervised probability distribution over each token within a sequence, conditioned on the sequence of tokens observed so far. We denote the random variable representing the next token as $x_t$ and the sequence of the tokens observed as $x_c$, i.e. language models compute $p(x_t|x_c)$.


For instance, in the unigram model, each word (token) $w_i$  is treated independently of each other and the probability of a sentence $w_1, w_2, ..., w_n$, is computed as the product of the probabilities of each word (see Equation \ref{unigram}).

\begin{equation}\label{unigram}
p(w_1, w_2, ..., w_n) = \prod_{i=1}^{n} p(w_i)
\end{equation}


Similarly the bigram model treats a sentence as pairs  $(w_1, w_2)$, $(w_2, w_3)$, ..., $(w_{n-1}, w_n)$. In such a way that the probability of a token is approximated as the probability of the token itself conditioned to its immediate predecessor. As in the unigram model, the probability of a sentence $w_1, w_2, ..., w_n$ is computed as the product of the probabilities of each token (see Equation \ref{bigram}).

\begin{equation}\label{bigram}
p(w_1, w_2, ..., w_n) = \prod_{i=1}^{n} p(w_i| w_{i-1})
\end{equation}

Generally we refer to the n-gram model, for a sequence of n words, where the probability of the sequence $p(w_1, w_2, ..., w_n)$ is approximated as the following.

\begin{align}
p(w_1, w_2, ..., w_n) &= p(w_1)p(w_2|w_1)p(w_3|w_{1:2}) ... p(w_n|w_{1:n-1})  \nonumber \\
 &= \prod_{i=1}^{n} p(w_i| w_{1:i-1})
\end{align}

For example for the sentence "A bank of fishes approaches":
\begin{equation}  
  \begin{aligned}
p(\text{``A bank of fishes approaches."}) = p(\text{``A"})\times&\\
p(\text{``bank"}|\text{``A"}) \times p(\text{``of"}|\text{``A bank"}) \times&\\
p(\text{``fishes"}|\text{``A bank of"}) \times &\\
p(\text{``approaches"}|\text{``A bank of fishes"})
  \end{aligned}
\end{equation}


If we were to produce the simplest embedding (sparse vector) for a text application, that would be the one-hot vector. To represent every word as an $\mathbb{R}^{|V| \times 1}$ vector with all 0s and one 1 at the index of that word in the sorted language vocabulary. In this notation, $|V|$ is the size of our vocabulary. 
Word vectors in this type of encoding would appear as the following:

\begin{equation*}
w^{aardvark} =
\begin{bmatrix}
  1\\
  0\\
  0\\
  \vdots\\
  0
\end{bmatrix}
w^{a} =
\begin{bmatrix}
  0\\
  1\\
  0\\
  \vdots\\
  0
\end{bmatrix}
w^{at} =
\begin{bmatrix}
  0\\
  0\\
  1\\
  \vdots\\
  0
\end{bmatrix}
\dotsb w^{zero} =
\begin{bmatrix}
  0\\
  0\\
  0\\
  \vdots\\
  1
\end{bmatrix}
\end{equation*}

\begin{equation*}
O = E \times T \times Q
\end{equation*}


![BERT fine tuning. The [CLS] token is a special symbol added in front of every input example, and [SEP] is a special separator token (e.g. separating questions/answers), from [@BERT]](./res/bert_fine_tuning.png){#fig:fine_tuning width=90%}


\begin{table}[!ht]
    \centering
    \begin{tabular}{|l|l|l|l|l|l|l|}
    \hline
        Gastos compartidos & ~ & ~ & ~ & ~ & ~ & ~ \\ \hline
        Concepto & Luis & Total & Concepto & Mar & Total & ~ \\ \hline
        Algo que Luis pagó & 327,65 € & Algo que Mar pagó & 82,71 € & ~ & ~ & ~ \\ \hline
        lidl & 3,88 € & finetwork & 25,00 € & ~ & ~ & ~ \\ \hline
        verduras & 8,55 € & iberdrola & 27,91 € & ~ & ~ & ~ \\ \hline
        verduras & 3,55 € & endesa & 15,90 € & ~ & ~ & ~ \\ \hline
        uber & 33,80 € & mercado san anton & 13,90 € & ~ & ~ & ~ \\ \hline
        uber & 27,70 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        lidl & 15,45 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        frutas & 17,85 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        primavera & 13,50 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        asia & 33,02 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        cerves & 30,00 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        lild & 10,33 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        corta & 5,90 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        panko & 32,75 € & ~ & ~ & ~ & ~ & ~ \\ \hline
        lidl & 91,37 € & ~ & ~ & ~ & ~ & ~ \\ \hline
    \end{tabular}
\end{table}


\begin{lstlisting}[style=pythonCodeStyle, label={p3}, caption={Third query for the meta-model. We ask for associations.}]
#include <iostream>
using namespace std;

int main() {
  int n;

  cout << "Enter an integer: ";
  cin >> n;

  if ( n % 2 == 0)
    cout << n << " is even.";
  else
    cout << n << " is odd.";

  return 0;
}
\end{lstlisting}