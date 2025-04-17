## 📝 TryHackMe Challenge – Official Write-Up  
**Author:** Natiq  
**Room Name:** UDP Lab – “Decoy in the Mist”  
**Difficulty:** Hard

---

### 🚀 Introduction

This room presents a deep dive into analyzing UDP services, identifying decoys, handling a memory vulnerability, and escalating privileges. From start to finish, it simulates a scenario where not everything is what it seems — and you’ll have to separate real threats from traps to succeed.

---

### 🔎 Reconnaissance

After a general reconnaissance of the target, several open services were discovered. Most of them responded strangely or inconsistently. This was the first clue that some ports might be decoys meant to confuse or even punish scanners.

Some ports would silently drop packets after a few attempts, while others would immediately render the attacker unreachable. The key here was **observation** — learning the behavior of each service before interacting further.

---

### 🎭 Identifying Decoys

Careful interaction with the services revealed an interesting pattern:
- One port would silently drop traffic after repeated contact.
- Another would respond once and then entirely block further communication.
- These behavioral clues suggested they were **honeypot-like decoys** with automated blocklisting mechanisms.

Understanding which services were “safe” to interact with was critical in progressing.

---

### 🧠 Exploiting the Vulnerability

One particular service behaved differently. It didn't shut us out or drop traffic. Upon closer inspection, interaction with this service led to instability, which hinted at a possible **memory corruption vulnerability**.

Crafting a payload triggered the vulnerability and granted initial access to the target. From there, enumeration revealed useful information that could be leveraged for privilege escalation.

---

### ⬆️ Privilege Escalation

Digging through the system uncovered a file with unusual permissions — a likely privilege escalation vector. The file’s logic was simple, but executing it successfully required careful setup.

Once exploited, this granted full administrative access to the system. As always, **enumeration is key**, and understanding your environment opens new doors.

---

### 🧩 Final Puzzle

The last challenge involved a hidden flag that wasn't directly accessible. The clue to retrieving it was stored securely — only those who had escalated their privileges and read between the lines would understand how to retrieve and decode it.

This tested not only technical skill but also the ability to think laterally, follow breadcrumbs, and adapt to unexpected constraints.

---

### 🏁 Conclusion

This room is a well-constructed labyrinth of misdirection, technical traps, and logical challenges. Success requires:
- Patience and observation
- Strong enumeration habits
- Knowing when to poke, and when to wait
- A good understanding of Linux internals and basic C vulnerabilities

Approach with caution, analyze everything, and enjoy the journey.

---

### 🛡️ Ethical Reminder

This write-up does not include any actual flags, specific port numbers, command outputs, or exploit code — in line with TryHackMe’s rules. It is intended for **educational purposes only** and to guide others in **approaching and thinking through challenges**, not to spoil them.

---
