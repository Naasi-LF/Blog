---
title: "Github_edu"
date: 2025-03-22T20:24:28+08:00
draft: false
description: "GitHub Copilot Tutorial"
tags: ["copilot"]
categories: ["Tutorial"]
---

# GitHub Copilot Student Authentication and Usage Guide (Taking CZUST Students as an Example)

## Difference Between UserName and Name

| **Aspect** | **Name**                                    | **Username**                        |
| :--------- | :------------------------------------------ | :---------------------------------- |
| **Definition**   | Display name (can be real name, e.g., XiCheng Yang) | GitHub account unique identifier (e.g., Naasi-LF) |
| **Purpose**   | Displayed on the profile or commit records | Used for logging into GitHub, personal page URL |
| **Uniqueness** | Not required to be unique | Must be unique |
| **Modification**   | Can be modified anytime | Can be modified, **but with caution** |

In practical usage, **Name** is your display information, more inclined to personal style; whereas **Username** is the technical identifier for your account, affecting your GitHub URL and account association.

When modifying your name, ensure that you're changing **Name**!!!

## Public Profile

In the **Settings**, modify the content to match the following:

![image-20250322194820049](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322194820049.png)

Ensure the homepage displays information as shown below:

![image-20250322194226134](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322194226134.png)

## Email Address

Add your school email address:

![image-20250322194506420](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322194506420.png)

Ensure you use the **czust.edu.cn** suffix instead of **czu.cn**.

## Payment Information

**No card binding required**, simply fill in the relevant payment details.

![image-20250322195308635](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322195308635.png)

## Two-Factor Authentication

Enable two-factor authentication (many might already have this).

![image-20250322195613116](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322195613116.png)

## Academic Authentication

Use [China Higher Education Student Information Network](https://www.chsi.com.cn/xlcx/index.jsp) for enrollment verification to download a PDF document like the one below.

![image-20250322200131384](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322200131384.png)

English content is best, Chinese content works fine.

Then **print** the document (convenient for taking photos with your phone).

## Start Application

Application must be done using your phone!!!!

Application must be done using your phone!!!!

Application must be done using your phone!!!!

Upon opening, avoid using a proxy (if unable to open, use mobile data).

Access the [Get your GitHub benefits - GitHub Education](https://education.github.com/discount_requests/application) website and log into your GitHub account.

![image-20250322200723915](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322200723915.png)

Select **Proof type** as "Other" (Academic verification from the above website belongs to "Other").

Enter a line of text: Type in the text box:
```
Ministry of Education online verification report
```

## Application Completion

Once your academic benefits are ready, you will receive an email notification ([GitHub benefits](https://link.zhihu.com/?target=https%3A//education.github.com/discount_requests/application) showing **Green Approved** on the right side means the application is approved but benefits are pending; **Purple Approved** indicates benefits have been granted. This process usually takes more than three days. After approval, you will receive an email notification).

![image-20250322200949658](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322200949658.png)

![image-20250322201118193](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322201118193.png)

## Subscription

This step is often overlooked!

After receiving GitHub Pro benefits, **Copilot will not automatically activate**. You need to subscribe manually; otherwise, you will still use the free version. Visit the [Subscription Page](https://link.zhihu.com/?target=https%3A//github.com/github-copilot/signup) and click "Subscribe."

![img](https://picx.zhimg.com/v2-3b1ff92b76530e4559bd24115cbd0823_1440w.jpg)

## Usage

### Method 1

Use the [GitHub Copilot Official Website](https://github.com/copilot/)

### Method 2

Download the Copilot plugin on VSCode (Pro Membership Required).

| **Operation**          | **Shortcut (Windows)** | **Shortcut (Mac)** | **Description**                          |
| ----------------------- | --------------------- | ------------------ | ---------------------------------------- |
| Activate Copilot        | Ctrl + Shift + P      | Cmd + Shift + P    | Open the Command Palette, search, and start Copilot. |
| Prompt Completion       | Alt + \               | Option + \         | Activate Copilot autocomplete.           |
| Show Code Suggestions   | Ctrl + Space          | Cmd + Space        | Provide code suggestions or autocomplete. |
| Insert Suggestions      | Tab                   | Tab                | Insert Copilot suggestions.              |
| Enable/Disable Copilot  | Ctrl + Shift + I      | Cmd + Shift + I    | Enable or disable Copilot.               |
| Show Copilot Dialog     | Ctrl + Enter          | Cmd + Enter        | Display Copilot dialog for interaction.  |
| View Full Suggestions   | Ctrl + .              | Cmd + .            | View full code suggestions from Copilot. |
| Access Copilot Settings | Ctrl + Shift + S      | Cmd + Shift + S    | Access Copilot settings for customization. |
| Reload Copilot          | Ctrl + Shift + R      | Cmd + Shift + R    | Reload the Copilot plugin configuration. |

**Pro Tip**: Use the **Tab key** for efficient work!

### Check Membership Status

If you can select preview models, this indicates membership.

![image-20250322201748314](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322201748314.png)

## Advanced Operations

### Scenario: Text to Image

Example text:

```bash
The defect tracking module builds an intelligent traceability system covering the entire detection process. Through deep integration of data flow monitoring, process backtracking, and warning intervention, it achieves visualized tracking and closed-loop management of the defect identification process. The module uses hierarchical architecture design to form a technical loop in full lifecycle management, real-time status sensing, and version control, ensuring full traceability from defect discovery to verification.
...
```

Create a `.tex` file in VSCode.

You can drag and drop relevant context into the file.

![image-20250322201941736](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322201941736.png)

Add prompts accordingly (divided into chat and edit functionality; chat mode outputs information to the chat box, while edit mode supports modifications, file creation, suitable for software project development but slower than chat mode).

**Details**: If image generation is required, you can use the GPT-4o model.

Compile the `.tex` file (use TeXLive + VSCode or Overleaf for compilation).

![image-20250322202801038](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322202801038.png)

The generated result might look unattractive.

![image-20250322202926552](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322202926552.png)

Since the output is a vector graphic, use tools like Adobe Acrobat DC for simple edits.

![image-20250322203807661](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322203807661.png)

After some tweaks, you can quickly upscale the image quality.