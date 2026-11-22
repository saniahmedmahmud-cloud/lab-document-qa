# Lab Document Q&A (practice project)

A small Python tool that answers questions using ONLY a text document,
shows which section the answer came from, and logs every question.
Built with made-up practice text, not real SOPs.

## What it does
1. Splits a document into sections.
2. Finds the section that shares the most words with the question.
3. Sends only that section to an AI model (Gemini) with strict rules.
4. Prints the answer and the source section.
5. Saves each question, source, answer and time to a log file.

## How to run
1. Install Python and the requests package (pip install requests).
2. Put your Gemini API key in a file named gemini_key.txt (one line, nothing else).
3. Put your document in sop_long.txt, with a blank line between sections.
4. Run lab_qa.py and type your questions. Type stop to finish.

## Safety design
- The model must answer only from the supplied section, or reply "Not found in the document."
- The document is treated as untrusted data, so instructions hidden inside it are ignored.
- The tool only reads. It cannot change or delete any file except its own log.
- The API key stays in a separate file and is never printed or written in the code.
- The source section is always shown, so a person can check the answer.

## Known limits
- Section search matches exact words only, so a differently worded question can miss.
- Free AI services are sometimes busy, so the tool retries and tries other models.
- Answers can still be wrong. Always check against the original document.
- Practice project only. Not for clinical decisions. Do not enter patient information.

## Files
- lab_qa.py: the program
- sop_long.txt: practice document (made up)
- qa_log.jsonl: log of questions (created when you run it)
