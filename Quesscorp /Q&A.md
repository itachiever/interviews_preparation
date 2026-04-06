1. How does the concept of **data integrity** at rest protect an ML pipeline from **data poisoning** before the training phase even begins?

**Answer:** Data integrity uses **digital fingerprints** to check if data changed. If a hacker alters the training data, the fingerprint breaks, stopping the bad data from entering the system.

2. Why does the concept of **deserializing** untrusted binary files pose an inherent **arbitrary code execution** risk in machine learning environments?

**Answer:** When loading a model file, the system unpacks it. A dangerous file can trick the system into **unpacking hidden malware** instead of just data, running it instantly.

3. Why does the traditional concept of **dynamic application security testing** fundamentally fail to detect **adversarial ML attacks** against inference endpoints?

**Answer:** Traditional tools send broken inputs to **crash the app**. Adversarial ML attacks send perfectly valid inputs designed to **trick the AI's brain**, which traditional tools do not understand.

4. In an ML architecture, how does defining a strict **trust boundary** between the feature store and the model registry prevent **supply chain tampering**?
**Answer:** A trust boundary acts like a **locked door**. It ensures that the system cleaning the data cannot touch the system storing the final model, preventing a hacker from swapping a good model with a bad one.

5. How does applying the concept of "**shift-left**" to Infrastructure as Code fundamentally change the economics of fixing **cloud misconfigurations**?
**Answer:** "Shift-left" means checking for mistakes in a **text file** before it becomes a live cloud server. Fixing a typo takes seconds, while fixing a live, running server is very expensive and risky.

6. How does the concept of **ephemeral**, just-in-time identity issuance eliminate the risk of **credential theft** in automated CI/CD pipelines?
**Answer:** Ephemeral identity gives a robot a **temporary name tag** that destroys itself after one task. Even if a hacker steals it, it will have already expired by the time they try to use it.

7. Since containers conceptually share the **host operating system kernel**, how does **user namespace remapping** prevent privilege escalation?
**Answer:** Containers share the underlying computer's brain. Remapping tricks the container into thinking it is the "boss", but the main computer still treats it like a **regular, powerless user**.

8. How does the concept of **taint analysis** in Static Application Security Testing differ from simple **pattern matching** for known bad functions?
**Answer:** Pattern matching just looks for **bad words** (like "delete_all"). Taint analysis follows the flow of data from user input to a dangerous action, understanding the context of how data moves.

9. How does the concept of **threat modeling** force a shift from identifying technical vulnerabilities to mapping out **business logic abuse**?
**Answer:** Instead of looking for code bugs, threat modeling asks "how can someone **abuse our business rules**?" (e.g., applying a $100 discount code 1,000 times), focusing on the logic rather than the technology.

10. How is the conceptual attack of **model extraction** different from traditional data exfiltration, and what **intellectual property** is actually compromised?
**Answer:** Data theft means stealing the customer list. Model extraction means asking the AI thousands of questions to secretly **rebuild a copy of the AI itself**, stealing the company's secret recipe instead of the data.

11. How does the **immutable layer** architecture of container images conceptually create a distinct attack surface for **hidden malicious code**?
**Answer:** Container images are built in **stacked layers**. A hacker can hide a tiny piece of malware in an old, hidden bottom layer that is hard to see, but still runs when the top layer starts.

12. Beyond simple encryption, how does the concept of **mutual cryptographic identity** verification prevent lateral movement in a microservices architecture?
**Answer:** Simple encryption hides the message, but mutual verification forces both apps to **show ID cards** to each other. If a hacker breaks into App A, App B will still reject it because the hacker lacks App A's ID.

13. How does the package resolution concept of "**most specific match wins**" enable dependency confusion attacks in internal ML libraries?
**Answer:** If an internal app asks for a tool, it might accidentally grab a **fake public version** with the exact same name from the internet because the system automatically prefers the publicly available package.

14. How does the concept of **asymmetric resource consumption** allow an attacker to bypass standard **rate-limiting** defenses on an ML API?
**Answer:** Rate limits block you after 10 requests. An attacker sends 10 normal-looking requests that force the AI to do **massive amounts of heavy math**, crashing the system completely while technically following the rules.

15. Why is the conceptual storage of declarative **infrastructure state files** inherently more sensitive than storing the configuration templates themselves?
**Answer:** A configuration template is just a **list of instructions** (like a recipe). The state file is the actual result (the baked cake), which often contains live passwords and IP addresses of the running system.

16. Why is serving a machine learning model directly from a data science notebook a violation of the principle of **least privilege**?
**Answer:** A notebook is a messy workshop with **all the tools and passwords** left out. The least privilege rule says a live model should only get exactly what it needs to answer questions, not the keys to the whole workshop.

17. How does the concept of a **hermetic**, immutable build environment prevent invisible supply chain compromises during the **software compilation** phase?
**Answer:** A hermetic environment is a completely **locked, clean room**. Nothing from the outside internet can sneak in during the building phase, guaranteeing that no hidden viruses are secretly added to the final product.

18. How does the concept of **transitive dependencies** exponentially increase the unmonitored attack surface in Python-based ML projects?
**Answer:** You install one safe tool, but that tool automatically downloads **five other hidden tools** it needs to work. You only checked the first tool, leaving the other five unchecked and potentially dangerous.
