## 前言

在王锐老师的指导下，阅读方向主要集中在脑电信号（EEG）深度学习模型，包括以下几篇代表性论文：

- **LaBraM (Large Brain Model)**  
- **BIOT: Biosignal Transformer for Cross-data Learning in the Wild**  
- **Neuro-GPT / EEG-GPT**  
- **EEGformer**  
- **PLM2EEG**  

基于这些方向，我整理了几篇核心论文及其信息如下：

---

## 核心论文与评价

1. **Large Brain Model for Learning Generic Representations with Tremendous EEG Data in BCI**  
   - **发表会议/期刊**：International Conference on Learning Representations 2024 (ICLR 2024)  
   - **CCF 2026 评级**：A（ICLR 属于人工智能 / 机器学习方向 A 类顶级会议）  

2. **EEGformer: A transformer–based brain activity classification method using EEG signal**  
   - **发表期刊**：Frontiers in Neuroscience  
   - **CCF 2026 评级**：未列入 CCF 核心推荐会议/期刊  
   - **说明**：Frontiers 系列为开放获取生物医学领域国际期刊，但不在最新 CCF 推荐的计算机科学核心会议或期刊名单内，因此通常不按 CCF A/B/C 评级。  

3. **BIOT: Biosignal Transformer for Cross-data Learning in the Wild**  
   - **发表会议/期刊**：NeurIPS 2023（Conference on Neural Information Processing Systems）主会稿件  
   - **CCF 2026 评级**：A（NeurIPS 是机器学习领域 A 类顶级会议）  

---

## 数据集获取

在阅读 **BIOT** 和 **LaBraM** 的过程中发现，其使用的 EEG 数据集来源于 Joe 教授团队（NEDC/TUH）。  
若想获取数据，需要向其团队提交申请。以下为与团队的邮件交流示例：  

> ### Download The TUH EEG Corpus
> **发件人**：严子熠 <1033230323@stu.jiangnan.edu.cn>  
> **收件人**：help <help@nedcdata.org>  
> **时间**：2026年3月17日(星期二) 下午5:11  
> **附件**：tuh_eeg.pdf  
>
> Dear NEDC Team,
>
> Please find attached my completed TUH EEG Subscriber Form.
>
> I have carefully filled in all required information, including my personal institutional address, contact details, and signature.
>
> Thank you for reviewing my application. I look forward to receiving the account credentials and access to the TUH EEG data.
>
> Best regards,  
> Ziyi Yan  
> School of Artificial Intelligence and Computer Science  
> Jiangnan University


> ### NEDC TUH EEG: credentials
> **发件人**：Joseph Picone <joseph.picone@gmail.com>  
> **收件人**：undisclosed-recipients  
> **时间**：2026年3月17日(星期二) 晚上9:29  
> **邮件处理**：已于 2026年3月19日(星期四) 上午9:56 回复  
>
> Dear TUH EEG User:
>
> Your application to access our resources has been approved. The next step is for you to generate an ssh key and send it to us. To do this, you will need to run the following command from a terminal window:
>
> ssh-keygen -t ed25519 -C "your.email@example.edu"
>
> Replace "your.email@example.edu" with the email address you listed on your application. It must be an institutional address - not a personal gmail, qq, or other such address.
>
> This command will prompt you for some information. Hit return four times, using defaults for all the values. This command will generate a file named id_ed25519.pub in your .ssh directory (or wherever your ssh tool stores its public keys).
>
> In this file, there is a line that contains:
>
> ssh-ed25519 <some random letters> <email address>
>
> Reply to this email and paste the contents of that ENTIRE LINE as plain text in the body of your message. We will add this information to our authorized keys file.
>
> Let us know if you have any questions.
>
> Best regards,  
> Joe Picone

> ### Re: NEDC TUH EEG: credentials
> **发件人**：严子熠 <1033230323@stu.jiangnan.edu.cn>  
> **收件人**：Joseph Picone <joseph.picone@gmail.com>  
> **时间**：2026年3月19日(星期四) 上午9:56  
>
> Dear Prof. Joe Picone,
>
> Thank you for approving my application. Here is my SSH public key as requested:
>
> ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIG/yi5vTOr19onwSe1NQDegxuiITDfi9bjhwzv9nZTtl 1033230323@stu.jiangnan.edu.cn
>
> Best regards,  
> Ziyi Yan

> ### NEDC TUH EEG: authorized users
> **发件人**：Joseph Picone <joseph.picone@gmail.com>  
> **收件人**：undisclosed-recipients  
> **时间**：2026年3月20日(星期五) 凌晨3:21  
> **附件**：example.txt  
>
> (Please remember to safelist our email addresses.)
>
> I have added your ssh key to our list of authorized users. Please test this command:
>
> ```bash
> rsync -auvxL -e "ssh -i ~/.ssh/id_ed25519" nedc-tuh-eeg@www.isip.piconepress.com:data/tuh_eeg/TEST .
> ```
>
> (all one line - see the attached file).
>
> Let us know if there are problems.
>
> -Joe
>
> =========
>
> **Subject**: NEDC TUH EEG: credentials  
> **Date**: Sun, 28 Dec 2025 23:15:19 -0600  
> **From**: Joseph Picone <joseph.picone@gmail.com>  
>
> Dear TUH EEG User:
>
> Your application to access our resources has been approved. The next step is for you to generate an ssh key and send it to us. To do this, you will need to run the following command from a terminal window:
>
> ```bash
> ssh-keygen -t ed25519 -C "your.email@example.edu"
> ```
>
> Replace "your.email@example.edu" with the email address you listed on your application. It must be an institutional address - not a personal gmail, qq, or other such address.
>
> This command will prompt you for some information. Hit return four times, using defaults for all the values.
>
> This command will generate a file named `id_ed25519.pub` in your `.ssh` directory (or wherever your ssh tool stores its public keys). Email this file to help@nedcdata.org as an email attachment. We will add your key to our database and notify you.
>
> Then you can test this using this command:
>
> ```bash
> rsync -auvxL -e "ssh -i ~/.ssh/id_ed25519" nedc-tuh-eeg@www.isip.piconepress.com:data/tuh_eeg/TEST .
> ```
>
> (all one line - see the attached file).
>
> This will download a file named `TEST` to your current working directory.
>
> Once you have verified this works, you can change `"data/tuh_eeg/TEST"` to any of the paths shown on this page:  
> [https://isip.piconepress.com/projects/nedc/html/tuh_eeg/](https://isip.piconepress.com/projects/nedc/html/tuh_eeg/)
>
> Please do not further disseminate this information or share it with other users. Ask them to register here:  
> [https://isip.piconepress.com/projects/nedc/html/tuh_eeg/](https://isip.piconepress.com/projects/nedc/html/tuh_eeg/)
>
> Please delete all older versions of our data that you have on your systems. The previous versions of the corpora have been obsoleted. Also remember to delete our data when you are done using it.
>
> Let us know if you have any questions.
>
> Best regards,  
> Joe Picone

> ### Re: NEDC TUH EEG: authorized users
> **发件人**：严子熠 <1033230323@stu.jiangnan.edu.cn>  
> **收件人**：Joseph Picone <joseph.picone@gmail.com>  
> **时间**：2026年3月21日(星期六) 上午8:42  
>
> Dear Prof. Joe Picone and the NEDC Team,
>
> Thank you so much for processing my application and granting me access to the TUH EEG Corpus.
>
> I am writing to confirm that I have successfully configured the SSH keys and started downloading the dataset via rsync. I deeply appreciate the detailed instructions you provided, which were extremely helpful.
>
> Thank you again for the tremendous effort your team puts into maintaining and sharing this invaluable dataset with the research community. I will strictly follow the data usage agreement, and I will certainly ensure that the TUH EEG Corpus and your related works are properly cited in our future publications.
>
> Best regards,  
> Ziyi Yan  
> School of Artificial Intelligence and Computer Science  
> Jiangnan University
---

## 记录理由

在此首先声明，我收集这些邮件和操作记录**完全出于学习目的**，与任何个人癖好无关。  

在邮件交流期间，我使用了 SSH、WinSCP 和 MobaXterm 等工具，但对这些工具并不熟悉。  
因此，我将这些过程整理、记录下来，以作为学习和研究的参考。  

日后，我也会继续记录自己的学习状态和操作经验，帮助自己回顾和总结，并形成完整的学习笔记