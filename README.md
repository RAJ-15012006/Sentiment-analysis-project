# Sentiment-analysis-project
This project analyzes text data to determine whether the sentiment is positive, negative, or neutral. It uses natural language processing (NLP) techniques to evaluate polarity (emotions/feelings) and subjectivity (opinion vs. fact). Example use cases include analyzing movie reviews, product feedback, or social media posts.

# Explanation about the project
1) pip install textblob — Installs the TextBlob library. In Colab, you can also write !pip install textblob. (The leading ! executes a shell command from a notebook cell.)
2) from textblob import TextBlob — Imports the TextBlob class used to compute sentiment.

 text -> it shall rain today — A comment illustrating an example input.

text = input(...) — Prompts the user to type a sentence; stores it in text.

print("analysis done") — Confirms that the input step completed.

tb_analyse = TextBlob(text) — Creates a TextBlob object; this wraps the text and enables NLP properties like .sentiment.

print(tb_analyse.sentiment) — Prints a Sentiment(polarity=..., subjectivity=...) tuple so you see both values together.

print('Polarity...', tb_analyse.sentiment.polarity) — Prints polarity (−1 to +1), indicating how negative/positive the text is.

print('Subjective...', tb_analyse.sentiment.subjectivity) — Prints subjectivity (0 to 1), indicating how opinionated the text is.

Example: "Today is a bad day" → polarity likely < 0 (negative), subjectivity > 0 (opinionated).

# 3)  lexix — Comment (intended as “lexicon demo”).

tb = TextBlob("I love Python, but bugs are terrible.") — Creates a TextBlob from a mixed‑sentiment sentence (contains both positive and negative words). You can inspect tb.sentiment, tb.sentiment.polarity, and tb.sentiment.subjectivity to see how lexicon scoring behaves on such text.

If you add print(tb.sentiment), you’ll see the computed polarity and subjectivity for this sentence.

4) print(reviews.keys()) — Displays available movie names (dictionary keys) so the user knows valid inputs.

movie_name = input(...) — Captures the movie to analyze.

if movie_name in reviews.keys(): — Guards against invalid names.

num = len(reviews[movie_name]) — Counts how many reviews exist for that movie.

print(f'The movie has {num} reviews') — Shows the count.

pos, neg, neu = 0, 0, 0 — Initializes counters.

for i in reviews[movie_name]: — Loops through each review. If your data is a tuple (text, rating), the text is at i[0].

tb_analyse = TextBlob(i[0]) — Creates a TextBlob for the review text.

if tb_analyse.sentiment.polarity > 0.05: — Uses a small positive threshold. Values just above 0 are treated as positive.

elif tb_analyse.sentiment.polarity < -0.05: — Values clearly below 0 are negative.

else: — Remaining values are neutral.

Final print(...) — Reports percentages of positive/negative/neutral reviews with consistent formatting.

else: print('Movie not in list') — Friendly error when the key isn’t found.

Why thresholds ±0.05? Tiny polarity values near 0 can be noise. Using a small band around 0 reduces false positives. You can tune these based on your dataset.

# Interpreting Results

Polarity close to +1.0 → strongly positive.

Polarity close to −1.0 → strongly negative.

Subjectivity close to 1.0 → highly opinionated; close to 0.0 → more factual.

In aggregate, the printed percentages summarize the overall tone of the reviews for the selected movie.

