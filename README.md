
# ILearnJapanese

  

### Insert cards for discord, travis, sonar, etc here.

  

## Table of Contents

1. [About](#about)
2. [Technology](#technology)
3. [Features](#features)
    1. [Vocabulary and Kanji Libraries](#feature.library)
    2. [Hiragana and Katakana Memorization](#feature.hira-kata)
    3. [Verb Particles](#feature.particles)
    4. [Conjugation](#feature.conjugation)
    5. [Vocab Memorization](#feature.vocab-mem)
    6. [Kanji Memorization](#feature.kanji-mem)

# About <a name="about"></a>

ILearnJapanese aims to be a one-stop-shop for studying Japanese.

  

Study modes will include Hiragana and Katakana Practice, Vocabulary Memory, Kanji Memory, Conjugation, Verb Particle Practice, and other miscellaneous study modes for different grammar concepts.

  

While designed specifically for the Genki textbooks, ILearnJapanese allows users to upload their own vocabulary and kanji sets to study as well.

  

Contributions are welcome of any kind, including assets, documentation, code, and feature requests.

  

This project is under the [GNU General Public License v3.0](https://choosealicense.com/licenses/gpl-3.0/).

# Technology <a name="technology"></a>

The ILearnJapanese website is planned to be a Vue Single-Page Application (located at `./ui`) using Bootstrap for styling. The site is compiled with Vite and served via AWS S3.

Any backend functionality is planned to be done via other AWS services. 
Because this is an open-source project, emphasis will be put on minimizing costs and using a stateless architecture.


# Features <a name="features"></a>

The below features are planned. However, there will likely also be a "miscellaneous" section for practicing more specific grammar concepts

## **Vocabulary and Kanji Libraries** <a name="feature.library"></a>

  

Users can upload Vocabulary and Kanji Libraries to study with. Libraries can have any number of sub-libraries, allowing for easier filtering of terms.

Sub-Libraries and Individual terms can be enabled and disabled, allowing users to disable terms they become familiar with as they study.

Study games will use the selected libraries in order to quiz users.
  

<details>

<summary>Example of a Vocabulary Entry</summary>

This is an example of what a vocabulary entry could look like:


```json
{
	"romanji": "keishain",
	"hiragana": ["けい","しゃ","いん"],
	"kanji": ["会","社","員"],
	"english": ["employee","office worker"],
	"categories": ["noun_generic","person","role"]
}
```

</details>

<details>

<summary>Example of a Kanji Entry</summary>

This is an example of what a kanji entry could look like:

```json
{
    "symbol": "一",
    "meaning": "one",
    "readings": ["いち","いっ","ひと"]
}
```
</details>

<details>

<summary>Example of a Library</summary>

This is an example of what a library could look like. Note that a Kanji library would use the same formatting:

```json
{
    "name": "Genki 1 Vocabulary",
    "description": "The first book of the Genki textbook series",
    "set": [
        {
            "name": "Lesson 1",
            "set": [
                // Vocabulary Terms go here...
            ]
        },
        {
            "name": "Lesson 2",
            "set": [
                // Vocabulary Terms go here...
            ]
        },
        // ...
    ],
}
```

</details>

## **Hiragana and Katakana Memorization** <a name="feature.hira-kata"></a>

Users select which hiragana and katakana characters they want to memorize by selecting from a table.

The website then chooses a random character and the user must write the correct answer.
For example, if the website displays `あ`, the user must respond with `a`.

An additional list is displayed to the side showing users the running percentage they get right, as well as which characters they have guessed incorrectly the most

## **Verb Particles** <a name="feature.particles"></a>

A verb and a term are given, and the user must enter the correct particle to use.

For example, `東京 ___ 行く` would be answered correctly if the user chose `に`

## **Conjugation** <a name="feature.conjugation"></a>

A verb and a form are given, and the user must enter the correct conjugation.

For example, with the verb `行く` and the form `short, negative, present`, the user must enter `行かない`

## **Vocabulary Memorization** <a name="feature.vocab-mem"></a>

The user selects different term/definition pairs. For example, if the user selected `English/Hiragana`, they would be given a word in English and must translate it into japanese using Hiragana.

Questions are either multiple choice or written, with the ability to enable and disable either option.

All selected vocab terms are added to a queue with the option of random shuffling. The term at the front of the queue is then displayed, and the user must either choose or write the correct "definition". When a user enters the incorrect answer, they must type out the correct answer three times. This term is then put back into the queue again and remains until answered correctly.

Users can restart at any time. They also have the option to toggle a statistics panel that displays their correct percentage as well as the top terms they get wrong. If `Kanji` is a selected term or definition, users will by default only need to answer using Kanji selected in their library. However, users can enable the option to require answering in full Kanji including symbols not selected in their libraries. 

## **Kanji Memorization** <a name="feature.kanji-mem"></a>

Kanji Memorization functions similarly to Vocabulary Memorization, but only allows for translating between a Kanji and its corresponding meaning. 

To practice translating Kanji into Hiragana or vice-versa, users should use the Vocabulary Memorization mode with `Kanji/Hiragana` selected as a term/definition pair, and a Kanji Vocabulary Library selected.