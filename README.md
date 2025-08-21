## MM PTM PPT Generator

An MCP tool to generate multiple PPTs for student Monthly PTMs without the trouble and pain of manually editing the same presentation multiple times :')

### why i built this

tl;dr: i hate making presentations

As an online tutor, I am required to prepare Parent-Tutor Meeting presentations every month - one per student. These slides summarize each student's progress, their diagnostic and test scores, practice data and areas to improve.

The process used to be:

- copy diagnostic school for 7 different Math strands from IXL
- manually paste IXL skill scores
- write learning gaps and action plans + notes
- mention stuff we did this month and what we plan on doing next
- fix formatting, alignment and typos (all the pain that comes with making presentations)

It was slow, repetitive and soo stressful - esp. when handling for multiple students.

I wanted a way where I could just type/copy the raw student data - paste all the IXL data without worrying about the terrible formatting on pasting, write without worrying about typos or structure.

Claude + this MCP made that possible.

- i copy/paste diagnostic and IXL data directly into Claude
- type student data and my notes in long free-form text (no worrying about structure)
- don't fix typos knowing that Claude is going to fix them for me

With this,

- placeholders like <code>{{Student}}</code>, <code>{{IXLAlgebraDiagnosticScore}}</code> or <code>{{LearningGaps}}</code> are replaced with the right info
- a ready-to-use PPT is generated in seconds <3

### how it works

1. The tool reads <code>template.pptx</code> (the ppt template i am supposed to use)
2. It scans for placeholders - written as <code>{{Placeholder_Name}}</code>
3. We provide student data in any form to Claude - it organizes it as JSON
4. The placeholders are replaced with correct data
5. A finished PPT is saved to <code>generated_ppts</code> folder

### setup and use
you'll need to use Claude desktop for running this mcp. turns out claude has great built in support for running mcps - the reason why i ended up using it.
1. clone the repo
<code>
git clone https://github.com/NishthaSharma-22/ppt-mcp
</code>

2. install dependencies
<code>pip install -r requirements.txt
cd mcp_ptm_ppt_generator
</code>

3. add mcp server to Claude desktop
in the project terminal, type:
<code>
fastmcp install claude-desktop mcp_ptm_ppt_generator.py --with python-pptx --with pydantic
</code>

4. head over to Claude desktop, go to <code>Settings &lt; Developer</code>. you should be able to see the mcp loaded there.

If claude shows errors while loading it, or something like 'server disconnected', which it likely will, close the application by going over to <code>file &lt; exit</code>
reopen the doc, and this should be fixed.

5. use inside claude!
you can now run the tool! i like to simply type <code>generate_ppt</code> and it prompts it to use the MCP to ask the required info. provide all the data - if something's missing it'll prompt you (great!) and you'll have a beautiful ppt within secs in <code>generated_ppts</code>

### future ideas:
- adding support for science ppt templates, since this is currently for math
- export directly to pdfs


#### notes
i had fun working on this, even though:
- i reloaded the mcp into claude like 100 times because of 'error:server-disconnected' 
- i edited the template.pptx way too many times to add those missing curly braces or fix the formatting. 
but at the end, it was satisfying and really worth it.
