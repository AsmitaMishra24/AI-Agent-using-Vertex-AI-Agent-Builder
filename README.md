# 🤖 Building a Travel Assistant AI Agent using Vertex AI Agent Builder

This guide explains how to build an AI-powered conversational agent using **Vertex AI Agent Builder** by Google Cloud. You'll learn to create a custom agent, configure its playbook, and enhance its responses by integrating a datastore.

---

## 📘 Table of Contents

- [🔧 Getting Started](#-getting-started)
  - [Step 1: Access Vertex AI Agent Builder](#step-1-access-vertex-ai-agent-builder)
  - [Step 2: Create a New App](#step-2-create-a-new-app)
  - [Step 3: Choose Agent Type](#step-3-choose-agent-type)
  - [Step 4: Set Up the Agent](#step-4-set-up-the-agent)
  - [Step 5: Define the Playbook](#step-5-define-the-playbook)
  - [Step 6: Test the Agent](#step-6-test-the-agent)

- [🧠 Adding Knowledge with Datastores](#-adding-knowledge-with-datastores)
  - [Step 7: Create a Tool](#step-7-create-a-tool)
  - [Step 8: Create a Datastore](#step-8-create-a-datastore)

- [🧩 Finalizing Agent with Datastore](#-finalizing-agent-with-datastore-step-by-step)
  - [Step 9: Refresh to View Datastore](#step-9-refresh-to-view-datastore)
  - [Step 10: Configure Grounding Settings](#step-10-configure-grounding-settings)
  - [Step 11: Confirm and Save Datastore](#step-11-confirm-and-save-datastore)
  - [Step 12: Attach Datastore to the Playbook](#step-12-attach-datastore-to-the-playbook)
  - [Step 13: Update Agent Instructions](#step-13-update-agent-instructions)

- [🧪 Final Testing](#-final-testing)

- [📌 Summary](#-summary)

- [🔗 Additional Resources](#-additional-resources)
  
- [📬 Contact](#-contact)

## 🔧 Getting Started

### Step 1: Access Vertex AI Agent Builder

- Go to [Vertex AI Agent Builder](https://makersuite.google.com/app).
- Click **Continue and Activate the API** on the welcome page.
![833886ce0d2645ba_1440](https://github.com/user-attachments/assets/79922b87-6f0b-4cf4-82fa-44b430b8bf9a)

### Step 2: Create a New App

- You'll be redirected to the App Creation page.
   ![Screenshot 2025-06-14 131228](https://github.com/user-attachments/assets/aa5cf373-7a7f-466b-a2fd-f645f19c9664)

- Click on **Create a New App**.
 
### Step 3: Choose Agent Type

- Select **Conversational Agent**.
- Click **Create**.
  ![Screenshot 2025-06-14 131307](https://github.com/user-attachments/assets/64c25f28-6083-41e7-80ec-7e4f9ccf2404)
> 💡 A new tab will open for Dialogflow Conversational Agents.  
> Select the correct Google Cloud project and enable the **Dialogflow API** if prompted.
  ![Screenshot 2025-06-14 131329](https://github.com/user-attachments/assets/7d68f739-920d-49f5-8d5b-554ba1155740)
- In the Dialogflow interface, click **Create Agent**.
  ![Screenshot 2025-06-14 131946](https://github.com/user-attachments/assets/8646793c-6459-4b9a-803e-dabf91c87c42)
- Choose **Build Your Own**.
  ![12](https://github.com/user-attachments/assets/b57b84c8-95c0-40f3-bf90-e866602e6896)

### Step 4: Set Up the Agent

- Enter a **Display Name** (e.g., `Travel Buddy`).
- Select **Global** as the region.
- Leave other settings as default.
- Click **Create**.
  <img width="755" alt="13" src="https://github.com/user-attachments/assets/69551aba-8929-4348-a7ec-08a17aef8daa" />


### Step 5: Define the Playbook

- Pick a **Playbook Name** (e.g., `Info Agent`).
- Add a **Goal** (e.g., `Help customers answer travel-related queries`).
- Define an **Instruction** (e.g., `Greet the user and ask how you can help today`).
- Click **Save**.
  ![Screenshot 2025-06-14 132931](https://github.com/user-attachments/assets/dc5626f0-577c-472c-b99d-c84275b29028)

### Step 6: Test the Agent

- Click the **Toggle Simulator** icon.
- Select your agent (e.g., `Info Agent`).
- Choose a model like `gemini-1.5-flash`.
  ![14](https://github.com/user-attachments/assets/4f7c922e-bac2-4c23-b707-8030bbf73835)
- Start a conversation using the **User Input** box.
  ![Screenshot 2025-06-14 132641](https://github.com/user-attachments/assets/b17a080c-0f98-4025-8ca4-b931926d03a5)

---

## 🧠 Adding Knowledge with Datastores

When users ask for unknown topics (e.g., *“How do I reach Wakanda?”*), it’s helpful to provide intelligent suggestions.
![Screenshot 2025-06-14 132931](https://github.com/user-attachments/assets/6c41dc3b-34ee-4d99-bcc7-cf42ef90a196)


### Step 7: Create a Tool

- On the Agent Basics page, scroll to the bottom.
- Click **+ Data store Tool**.
  ![Screenshot 2025-06-14 132959](https://github.com/user-attachments/assets/904fc7af-9672-4b59-8e22-0a9062dbab69)

- Fill in:
  - **Tool Name:** `Alternative Location`
  - **Type:** Data store
  - **Description:** `Use this tool if the user's request contains a location that doesn't exist`
- Click **Save**.
  ![Screenshot 2025-06-14 133518](https://github.com/user-attachments/assets/41e970e6-73b6-49ac-bab9-cd21f6760cc4)

### Step 8: Create a Datastore

- Click **Add Data Stores** → **Create Data Store**.
  ![Screenshot 2025-06-14 133651](https://github.com/user-attachments/assets/460e6796-c257-48b1-a913-9abc3dc9c203)
- Choose **Cloud Storage**.
  ![16](https://github.com/user-attachments/assets/b6c985f3-67e7-4571-90b7-c762656f812d)

- Under **FILE**, enter: ai-workshops/agents/data/wakanda.txt
  ![Screenshot 2025-06-14 133808](https://github.com/user-attachments/assets/e730220b-4b30-4854-a004-4c5d687ccff3)

- Click **Continue**.

📁 **Example Contents of wakanda.txt**
- Places that are similar to Wakanda:
  - Oribi Gorge, South Africa
  - Iguazu Falls, Argentina/Brazil
  - Disney’s Marvel Day at Sea


- Name the datastore (e.g., `Wakanda Alternative`) and click **Create**.
  ![Screenshot 2025-06-14 133908](https://github.com/user-attachments/assets/3876fda0-37b2-4659-b88f-bd30d2aaa790)


> Wait for the import process to complete. You can track it in the datastore dashboard.
![Screenshot 2025-06-14 134551](https://github.com/user-attachments/assets/f890ef82-5c39-4c4b-9c5d-130e41ef3678)
![Screenshot 2025-06-14 134601](https://github.com/user-attachments/assets/7003e104-d442-42ab-b51f-a4911479235f)

---

## 🧩 Finalizing Agent with Datastore: Step-by-Step

### Step 9: Refresh to View Datastore
After your datastore is created and imported:
- Go back to your **Dialogflow** tab.
- Click **Refresh**.
- You should now see your datastore under **Available data stores**.
![a44373b78bd95ff0_1440](https://github.com/user-attachments/assets/0395c780-20f7-45ae-bf08-21b0a31e7655)

---

### Step 10: Configure Grounding Settings

- To reduce hallucinations, set the grounding configuration for the datastore to **Very Low**.
  ![Screenshot 2025-06-14 134853](https://github.com/user-attachments/assets/fbb7bad7-460a-49a9-852a-2044eedb84ac)

- This ensures the agent doesn't generate inaccurate or made-up answers.
- For now, leave it at **default**, but explore the grounding options later.

---

### Step 11: Confirm and Save Datastore

- Select the added datastore from the list.
  ![40082aebe8b82d7c_1440](https://github.com/user-attachments/assets/236493c8-fca5-4d79-9bf0-5fb371b36927)
- Click **Confirm**.
- Then click **Save** to apply the changes.

---

### Step 12: Attach Datastore to the Playbook

- Go to your **Agent Basics** page.
  ![17](https://github.com/user-attachments/assets/6d7297d7-40c5-4ad2-8428-381db69efb15)
- Scroll to the bottom under **Playbook Configuration**.
- Your newly created datastore (e.g., `Alternative Location`) should appear.
  ![Screenshot 2025-06-14 135330](https://github.com/user-attachments/assets/098ad605-31be-48af-afeb-e316b641873a)
- Check the box next to the datastore.
- Click **Save** at the top of the page.
    ![18](https://github.com/user-attachments/assets/0ca3e2ad-9dc3-4ae3-9dda-0fa893ec1cef)

---

### Step 13: Update Agent Instructions

To ensure your agent knows how to use the datastore:

- Add the following line to the **Instructions** field in the Playbook:
```
    Use ${TOOL: Alternative Location} if the user's request contains a location that does not exist
```

- Click **Save** to apply the updated instructions.
![19](https://github.com/user-attachments/assets/1a1fde2c-d8b9-4892-bd80-7c623adb5503)
---

## 🧪 Final Testing

- Reopen the **Toggle Simulator**.
- Select your agent (e.g., `Info Agent`).
- Choose the model (e.g., `gemini-1.5-flash`) if prompted.
  ![14](https://github.com/user-attachments/assets/54746186-3cec-4270-b58e-54d34226c665)

- Start Conversation and ask your agent:  
  **“What’s the best way to reach Wakanda?”**

> 🎉 Your agent now gives intelligent recommendations using external knowledge from your custom datastore.
  ![google ai gemini workshop](https://github.com/user-attachments/assets/6576e164-a9f1-4e9c-8a8d-c7b41f0da2ec)
---

## 📌 Summary

You have successfully:

- Created a conversational agent using Vertex AI.
- Configured goals, instructions, and responses.
- Extended agent knowledge using a custom datastore.
- Simulated and tested interactions using real inputs.

---

## 🔗 Additional Resources

- [Vertex AI Documentation](https://cloud.google.com/vertex-ai)
- [Dialogflow Documentation](https://cloud.google.com/dialogflow)
- [Vertex AI Agent Builder Guide](https://cloud.google.com/vertex-ai/docs/agent-builder/overview)

## 📬 Contact

Made by **Asmita Mishra**
- 🔗 [LinkedIn](https://www.linkedin.com/in/asmitamishra1/)  
- 💻 [GitHub](https://github.com/AsmitaMishra24)  

🙋‍♀️ **Have a suggestion or found a bug?**  
- Feel free to [**raise an issue**](https://github.com/AsmitaMishra24/Employee-Directory-Application-using-AWS/issues) in this repository.

📩 **Want to connect or collaborate?**
- Feel free to reach out via [LinkedIn](https://www.linkedin.com/in/asmitamishra1/)
---
