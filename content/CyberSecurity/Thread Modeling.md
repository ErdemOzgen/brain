
**STRIDE** is a model for identifying [computer security](https://en.wikipedia.org/wiki/Computer_security "Computer security") [threats](https://en.wikipedia.org/wiki/Threat_(computer) "Threat (computer)")[[1]](https://en.wikipedia.org/wiki/STRIDE_model#cite_note-1) developed by Praerit Garg and [Loren Kohnfelder](https://en.wikipedia.org/wiki/Loren_Kohnfelder "Loren Kohnfelder") at [Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft").[[2]](https://en.wikipedia.org/wiki/STRIDE_model#cite_note-2) It provides a [mnemonic](https://en.wikipedia.org/wiki/Mnemonic "Mnemonic") for security threats in six categories.[[3]](https://en.wikipedia.org/wiki/STRIDE_model#cite_note-3)

The threats are:

- [**S**poofing](https://en.wikipedia.org/wiki/Spoofing_attack "Spoofing attack")
- [**T**ampering](https://en.wikipedia.org/wiki/Tampering_(crime) "Tampering (crime)")
- [**R**epudiation](https://en.wikipedia.org/wiki/Non-repudiation "Non-repudiation")
- **I**nformation disclosure ([privacy breach](https://en.wikipedia.org/wiki/Data_privacy "Data privacy") or [data leak](https://en.wikipedia.org/wiki/Data_leak "Data leak"))
- [**D**enial of service](https://en.wikipedia.org/wiki/Denial-of-service_attack "Denial-of-service attack")
- [**E**levation of privilege](https://en.wikipedia.org/wiki/Privilege_escalation "Privilege escalation")[[4]](https://en.wikipedia.org/wiki/STRIDE_model#cite_note-4)

Each threat is a violation of a desirable property for a system:

|Threat|Desired property|Threat Definition|
|---|---|---|
|Spoofing|[Authenticity](https://en.wikipedia.org/wiki/Message_authentication "Message authentication")|Pretending to be something or someone other than yourself|
|Tampering|[Integrity](https://en.wikipedia.org/wiki/Data_integrity "Data integrity")|Modifying something on disk, network, memory, or elsewhere|
|Repudiation|[Non-repudiability](https://en.wikipedia.org/wiki/Non-repudiation "Non-repudiation")|Claiming that you didn't do something or were not responsible; can be honest or false|
|Information disclosure|[Confidentiality](https://en.wikipedia.org/wiki/Confidentiality "Confidentiality")|Someone obtaining information they are not authorized to access|
|Denial of service|[Availability](https://en.wikipedia.org/wiki/Availability "Availability")|Exhausting resources needed to provide service|
|Elevation of privilege|[Authorization](https://en.wikipedia.org/wiki/Authorization "Authorization")|Allowing someone to do something they are not authorized to do|



### [The CIA Triad](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/threat-modeling.html#the-cia-triad)

The CIA Triad is a widely recognized model in the field of information security, standing for Confidentiality, Integrity, and Availability. These three pillars form the foundation upon which many security measures and policies are built, including threat modeling methodologies.

1. **Confidentiality**: Ensuring that the data or system is not accessed by unauthorized individuals. This is a central aspect of security, requiring appropriate access controls, encryption, and other measures to prevent data breaches.
2. **Integrity**: The accuracy, consistency, and trustworthiness of the data over its lifecycle. This principle ensures that the data is not altered or tampered with by unauthorized parties. It often involves checksums, hashing, and other data verification methods.
3. **Availability**: This ensures that data and services are accessible to authorized users when needed. This often involves redundancy, fault tolerance, and high-availability configurations to keep systems running even in the face of disruptions.




### [Threat Modeling Methodlogies](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/threat-modeling.html#threat-modeling-methodlogies)

1. **STRIDE**: Developed by Microsoft, STRIDE is an acronym for **Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege**. Each category represents a type of threat, and this methodology is commonly used in the design phase of a program or system to identify potential threats.
2. **DREAD**: This is another methodology from Microsoft used for risk assessment of identified threats. DREAD stands for **Damage potential, Reproducibility, Exploitability, Affected users, and Discoverability**. Each of these factors is scored, and the result is used to prioritize identified threats.
3. **PASTA** (Process for Attack Simulation and Threat Analysis): This is a seven-step, **risk-centric**methodology. It includes defining and identifying security objectives, creating a technical scope, application decomposition, threat analysis, vulnerability analysis, and risk/triage assessment.
4. **Trike**: This is a risk-based methodology that focuses on defending assets. It starts from a **risk management** perspective and looks at threats and vulnerabilities in that context.
5. **VAST** (Visual, Agile, and Simple Threat modeling): This approach aims to be more accessible and integrates into Agile development environments. It combines elements from the other methodologies and focuses on **visual representations of threats**.
6. **OCTAVE** (Operationally Critical Threat, Asset, and Vulnerability Evaluation): Developed by the CERT Coordination Center, this framework is geared toward **organizational risk assessment rather than specific systems or software**.

