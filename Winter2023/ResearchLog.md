<!-- 
✅ - complete
⏰ - in progress
❌ - struggle / cannot complete
-->

# Winter 2023 Research Log

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#weekly-updates">Weekly Updates</a>
      <ol>
        <li><a href="#week-one">Week One</a></li>
      </ol>
    </li>
    <li><a href="#key-findings">Key Findings</a></li>
    <li><a href="#possible-solutions">Possible Solutions</a></li>
    <li><a href="#glossary">Glossary</a></li>
    <li><a href="#overall-questions">Overall Questions</a></li>
  </ol>
</details>

**Key:**
✅ - complete | ⏰ - in progress | ❌ - struggle / cannot complete
<!-- Weekly Updates -->
## Weekly Updates
### Week One

###### *Dates:* January 8-14, 2024

###### *Main Objective:* Begin to understand ArangoDB and OpenCypher codebase

#### Team Tasks:
1. ✅ Reorganize GitHub
2. ✅ Fork [OpenCypher](https://github.com/opencypher/openCypher) and [ArangoDB](https://github.com/arangodb/arangodb).
3. ❌ Setup Dockerfile so ArangoDB and OpenCypher will work on all machines. 
    - At least try and setup ArangoDB on machine (Will's), step in the right direction.
4. Beginning looking into documentation for both [OpenCypher](https://s3.amazonaws.com/artifacts.opencypher.org/openCypher9.pdf) and [ArangoDB](https://docs.arangodb.com/3.11/aql/). 
5. ✅ Find CFG implementations in both codebases. 
6. ⏰ Begin to understand how the CFG works in parallel with the rest of the codebase.
7. Reach out to the teams of both and ask if they have the feature we are looking for. 
8. ✅ Update pushing functionality for both repos.
9. Look into the CFGs in both and try to understand them. 

#### Individual Tasks:
1. Wyatt - research and understand CFGs

#### In Progess:
- Working on creating a Dockerfile to run both ArangoDB and OpenCypher on different devices.

#### Accomplishments:
- January 10th: 
  - rearranged GitHub to be more friendly towards the year's project. Added space for research logs and key findings, glossary, etc.
- January 12th: 
  - forked codebases for both ArangoDB and OpenCypher, [arangodb_esrp](https://github.com/wrcorcoran/arangodb_ersp) and [opencypher](https://github.com/wrcorcoran/openCypher_ersp).
  - updated README.md for both and added collaborators along with proper permissions.
  - located directory for grammars in both codebases.
- January 13th:
  - located ```grammar_tools```, which the Grammar specifications by openCypher. 
  - Tried to run both ArangoDB and OpenCypher's GitHubs and ran into errors for both. See ```Struggles``` for more information.
  - Working on following the ArangoDB specifications for contributing ()

#### Specific Questions:
- What is Gherkin? Encountered it while looking into the OpenCypher codebase.
- How are we supposed to use ArangoDB if we have to pay? Also, there seems to be no option to use it strictly in terminal, so do we have to craft that ourself?

#### Relevant Papers / Links:
- [ArangoDB Github](https://github.com/arangodb/arangodb)
- [ArangoDB documentation](https://docs.arangodb.com/3.11/aql/)
- [OpenCypher Github](https://github.com/opencypher/openCypher)
- [OpenCypher documentation](https://s3.amazonaws.com/artifacts.opencypher.org/openCypher9.pdf)
- [Context free schemas for data-XML (important for OpenCypher)](https://www.w3.org/People/Bos/Schema/schemas)
- [Indicated as Syntax Tree Template by OpenCypher](https://www.w3.org/2001/XMLSchema)
- [Cypher Railroad Diagram of Grammar](https://s3.amazonaws.com/artifacts.opencypher.org/M23/railroad/Cypher.html)
- [Cypher Specific Style Guide](https://s3.amazonaws.com/artifacts.opencypher.org/M23/docs/style-guide.pdf)
- [ArangoDB Contributing Guide (includes building specifications)](https://github.com/arangodb/arangodb/blob/devel/CONTRIBUTING.md#building)

#### Notes:
- ArangoDB grammar is found in 'arangod/grammar.cpp' and 'arangodb/grammar.hpp' and 'grammar.y'. Have not identifying the exact files (and what they do), but that will be the next step.
- OpenCypher's grammar is found under 'grammar' (wow!). Includes a README.md with specifics about the grammar.

#### Struggles:
- Running into Maven build errors when trying to execute the ```mvn -U clean install -P scala-213 -Dlicense.skip``` command. Unsure if this is because of something I don't have installed correctly or a dependency failure further up.
  - The specific error is ```org.apache.maven.plugins:maven-compiler-plugin:3.8.1:compile (default-compile) on project grammar: Fatal error compiling: invalid target release: 11 -> [Help 1]```. I've ran it in debug mode and get messages that are relatively unreadable. Not sure where to go here.
- Likewise, ArangoDB requires an account to run. 

<!-- Key Findings -->
## Key Findings
Currently, none.

<!-- Possible Solutions -->
## Possible Solutions
Currently, none.

<!-- Glossary -->
## Glossary
Currently, none.

<!-- Questions -->
## Overall Questions
Currently, none.