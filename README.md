# SJTU-APT23
Considering the issues of outdated and limited coverage in existing open-source APT traffic datasets, we have compiled a comprehensive APT traffic dataset named SJTU-APT23, which includes over 700 traffic files from 25 APT organizations. This involves two main parts: the construction of an APT malware sample corpus and the collection of APT malicious traffic data.

## Construction of the APT Malware Sample Corpus
To ensure that the APT traffic we collect is up-to-date, we first obtain the latest and still active APT samples. These samples are sourced from the open platforms VirusTotal\cite{virustotal} and MalwareBazaar\cite{MalwareBazaar}.

VirusTotal is a threat intelligence sharing platform that detects approximately 400K malicious files per day on average\cite{alrawi2021circle} and counts the number of security vendor engines marking the files as malicious\cite{dodia2022exposing}. We collected 4,945 labeled APT samples through various searches and filtered them using VirusTotal's malicious score. We excluded 671 samples with scores below 15, leaving samples with a median score of 39 (range 16-62), indicating high likelihood of being malicious APT samples.

MalwareBazaar is a platform for sharing malware, averaging around 400 new malware samples shared per day, with over 700,000 samples shared in total. It provides basic sample information and supports keyword searches. Using its API, we collected 668 APT samples from 51 organizations, filtering out those without organizational tags and standardizing aliases.

By consolidating samples from these two sources, we compiled a total of 4696 APT samples from 68 organizations, achieving broad coverage.

## Collection of APT Malicious Traffic
We selected Falcon Sandbox\cite{Hybrid} and ANY.RUN\cite{ANYRUN}, two open-source sandboxes. Falcon Sandbox, from Hybrid Analysis, is an open-source malware analysis tool supporting various environments and file types, with batch analysis options and pcap traffic capture. ANY.RUN is an interactive platform analyzing network behavior, process states, file, and registry activities, offering real-time feedback and generating a pcap file for the execution process.We developed a crawler system to run scripts daily from January to April 2023 to complete the traffic collection.

Most crawled traffic was invalid or noisy, with some samples evading analysis by generating minimal packets. We filtered out pcap files smaller than 4KB. Additionally, we removed those lacking TCP/UDP protocols and files with failed TCP connections or no further activity, considering the unpredictable nature of APT malware and the presence of noisy ARP and NBNS requests.

Ultimately, we obtained 726 valid pcap files from 4696 APT samples, totaling 427MB. Due to high manual screening costs, we filtered data for only 25 organizations. This dataset, named SJTU-APT23, is the most comprehensive APT traffic dataset to date, covering the widest range of APT organizations. The composition of the dataset is shown in Table \ref{SJTU-APT23}, and the organizational distribution is illustrated in Figure \ref{SJTU-APT23饼图}.

<img src="https://github.com/zhm0203/SJTU-APT23/blob/main/SJTU-APT23.png" width="380" height="250" />
