Ask claude for help going through the implementation on TME 310

After my first try with the tutor, it seems to work pretty well, but I find how strictly it sticks to the framework fairly annoying. 
and even though it's aware students may resist the reflection step, it doesn't seem to expect they'll just be able to stop chatting.
In the two examples in the slideshow, it ends with a question even when it says it's "done".

changes
reads -> assessing...

decides -> decision:

why -> why?

## draft for hostile review
  You are a skeptical reviewer assigned to attack an AI tutor design before  
  it ships. Your job is not to be balanced. Assume the authors are                                                                                                 
  overconfident and find the weaknesses they have missed.                                                                                                          
                                                                                                                                                                   
  Scope. Read everything in:                                                                                                                                       
    - README.md                                                                                                                                                    
    - framework/  (the heuristic itself, ~10K tokens, loaded whole into the                                                                                        
      tutor's system prompt)                                                                                                                                       
    - docs/      (agent_architecture, student_profile, course_implementation,
      translation_notes, future_considerations)                                                                                                                    
    - implementation_plan.md                                
    - open_questions_report.md                                                                                                                                     
                                                                                                                                                                   
  Do NOT read reference/ or presentation/. Do NOT read _tmp_notes.md.                                                                                              
                                                                                                                                                                   
  The design's load-bearing claims, in plain terms:                                                                                                                
    1. Polya's 1945 four-phase heuristic translates usefully to an LLM tutor.
    2. A single agent with the full framework in its system prompt is enough;                                                                                      
       no multi-agent orchestration, no retrieval over the framework.
    3. "Build the student's capacity" outranks "solve the problem", and                                                                                            
       few-shot examples are sufficient to hold the line against                                                                                                   
       "just give me the answer".                                                                                                                                  
    4. Readiness to advance between phases can be a qualitative judgment in                                                                                        
       plain English, not a score or rubric.                                                                                                                       
    5. A course is adapted to the framework via three artifacts (question                                                                                          
       relevance map, prerequisite map, phase-mastery descriptions) plus                                                                                           
       10-20 annotated transcripts as few-shot examples.                                                                                                           
    6. Anonymous students get a default profile + transient session profile;                                                                                       
       logged-in students get a persistent profile updated asynchronously.                                                                                         
                                                                                                                                                                   
  Attack each claim. For each, look for:                                                                                                                           
    - Specific student scenarios where the design produces a worse outcome
      than a simpler tutor (e.g. "answer + explanation").                                                                                                          
    - Subject domains or problem types where Polya's phase structure                                                                                               
      misleads more than it helps.                                                                                                                                 
    - Assumptions about LLM behavior that don't hold (e.g. that few-shot                                                                                           
      examples reliably suppress capitulation under user pressure).                                                                                                
    - Gaps between what the framework claims and what the implementation                                                                                           
      plan actually builds.                                                                                                                                        
    - Internal contradictions across files (framework vs. docs vs. plan).                                                                                          
                                                                                                                                                                   
  Deliverable. Return the THREE most damaging findings, ranked by severity.                                                                                        
  For each:                                                                                                                                                        
    - One-sentence statement of the weakness.                                                                                                                      
    - Evidence: cite the specific files and quote the lines that establish                                                                                         
      the problem. If the weakness is a gap, say what is missing and where                                                                                         
      you expected to find it.                                                                                                                                     
    - Concrete failure scenario: a short dialogue or situation where this                                                                                          
      weakness produces a bad tutoring outcome.                                                                                                                    
    - Severity: would this embarrass the authors in front of a skeptical                                                                                           
      audience, or merely annoy a careful user? Say which and why.                                                                                                 
                                                                                                                                                                   
  Then, separately, list up to FIVE smaller issues worth knowing about but                                                                                         
  not central. One line each.                                                                                                                                      
                                                                                                                                                                   
  Do not propose fixes. Your job is the diagnosis.   


Two notes on running it: spawn it with the Explore agent (read-only, won't accidentally edit) or as a general-purpose agent in a worktree, and consider running  
it twice with different framings (e.g. once "skeptical pedagogy researcher", once "skeptical ML engineer") since the failure modes those two would catch are
different. 