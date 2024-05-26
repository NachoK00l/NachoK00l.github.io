---
title: I am learning Javascript!
date: 2024-05-26 16:12:00 +0200
categories: [Javascript]
tags: [Javascript, learning]
---

Today I decided to start learning Javascript, by making a small tool. I decided to make a character counter.

I started by making a basic character counter. It counts the amount of characters in a string.

```Javascript
function updateText() {
    let outputLabel = document.getElementById("output");
    let textField = document.getElementById("input");

    let text = textField.value;
    let count = text.length;
    outputLabel.innerText = count;
}
```

This script takes the input from a <textarea> and counts the amount of characters in it.

Here is a preview:

![Character counter preview](/assets/images/learning-javascript/characterCounter.gif){: .shadow }

Then I added a word counter.

```Javascript
function updateWordCount(){
    let wordLabel = document.getElementById("wordCount");
    let textField = document.getElementById("input");

    let text = textField.value;

    let words = text.split(" ");

    let wordCount;
    if (words[words.length - 1] == "") {
        wordCount = words.length - 1;
    } else {
        wordCount = words.length;
    }

    wordLabel.innerHTML = wordCount;
}
```	

This code splits the text into words and counts the amount of words. It also ignores empty strings. This is so that if you type a sentence with a space at the end, it won't count the empty string as a word.

Here is a preview:

![Word counter preview](/assets/images/learning-javascript/wordCounter.gif){: .shadow }

As a last feature, I added a "Common words" list. This list shows the top 10 most common words in your text.

```Javascript
function updateWordList() {
    let wordListHolder = document.getElementById("wordList");
    let textField = document.getElementById("input");

    let wordList = getWordCount(textField.value.toLowerCase().split(" "));

    for (item of sortDictionary(wordList).slice(0, 10)) {
        wordListHolder.innerHTML += `
        <p class="center">${capitalizeFirstLetter(item)}: ${wordList[item]}</p>`;
    }
}
```

It first gets a list of the words in the text. Then it creates a dictionary with the words as keys and the amount of times they appear as values. Then it sorts the dictionary by the amount of times they appear, and it gets the top 10 words.

Here is a preview:

![Word list preview](/assets/images/learning-javascript/wordList.gif){: .shadow }

This is a realy simple tool, but I think it's a good start to learn Javascript. I hope you enjoy it!

Want to try my tool out? You can find it [here](https://nacho.cool/javascript-tools/character-counter).

Want to check the source code? You can find it [here](https://github.com/NachoK00l/javascript-tools).