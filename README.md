<div align="center">
  <br />
  <a href="https://www.imghippo.com/i/ZK4zy1722288141.jpg" title="Project Screenshot" target="_blank">
    <img src="https://i.imghippo.com/files/ZK4zy1722288141.jpg" width="100%" alt="Project Screenshot"/>
  </a>
  <br />
  <div>
    <img src="https://img.shields.io/badge/-JavaScript-black?style=for-the-badge&logoColor=white&logo=javascript&color=F7DF1E" alt="javascript" />
    <img src="https://img.shields.io/badge/-Gemini AI-black?style=for-the-badge&logoColor=white&logo=gemini&color=412991" alt="gemini ai" />
  </div>
  <h3 align="center">AI Cancer Care (BeatCancer: AI Assistant to Craft Personalized Cancer Care)</h3>
  <div align="center">
    Welcome to the AI Cancer Care project, a revolutionary AI assistant designed to provide personalized cancer care by analyzing patient data, guidelines, and medical records. Our goal is to identify screening gaps and create tailored treatment plans to improve patient outcomes.
  </div>
</div>

## 📋 Table of Contents

1. 🤖 [Introduction](#introduction)
2. 🔋 [Features](#features)
3. 🏆 [Inspiration](#inspiration)
4. ⚙️ [Setup and Deployment](#setup-and-deployment)
5. 🚀 [Usage](#usage)
6. 🌠 [Gemini AI Integration](#gemini-ai-integration)
7. 🤝 [Contributing](#contributing)
8. 📜 [License](#license)

## 🤖 Introduction

AI Cancer Care provides an easy and efficient way to craft personalized cancer care using AI. It interacts with the Gemini AI to analyze and generate detailed treatment plans based on patient data and medical records.

## 🔋 Features

- **Personalized Treatment Plans**: Analyzes patient data, medical records, and guidelines to identify gaps in cancer screening and follow-up care, crafting tailored treatment plans for individual patients.
- **Secure Data Sharing**: Shares sensitive data securely using encryption and cryptographic features, protecting patient information while facilitating necessary data access for healthcare providers.

## 🏆 Inspiration

This project is deeply personal to me. My grandmother recently passed away from cancer, and witnessing her struggle firsthand inspired me to create a solution that could help others in similar situations. She often faced difficulties in coordinating her care and keeping track of her treatment plan, which sometimes led to missed appointments and delayed treatments. I wanted to build an application that could alleviate these challenges for other patients and their families.

## ⚙️ Setup and Deployment

### Prerequisites

- Node.js and npm installed

### Steps

1. **Clone the Repository**

   ```bash
   git clone https://github.com/mendsalbert/beat-cancer.git
   cd beat-cancer
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Setup Environment Variables**

   Create a `.env` file in the root directory with the following content:

   ```plaintext
   VITE_GEMINI_API_KEY='Gemini api key here'
   ```

4. **Build the Project**

   ```bash
   npm run build
   ```

## 🚀 Usage

1. **Upload Reports**: Patients or healthcare providers can upload medical reports directly into the system.
2. **View Treatment Plan**: The AI assistant generates a detailed treatment plan based on the uploaded data and identified gaps.
3. **Track Progress**: Patients can monitor their progress, completed screenings, and upcoming appointments through a user-friendly dashboard.

## 🌠 Gemini AI Integration

Incorporating Gemini AI into our system provides additional layers of analysis and generative capabilities:

- **Detailed Image Analysis**: Gemini AI can process medical images uploaded by patients or healthcare providers, offering advanced diagnostic insights.
- **Advanced Natural Language Processing**: Enhances the accuracy of treatment plans and patient data analysis.
- **Scalable AI Infrastructure**: Leveraging Gemini AI's robust infrastructure allows for real-time data processing and analysis.

### Example of Using Gemini AI:

```javascript
import { GoogleGenerativeAI } from "@google/generative-ai";

const genAI = new GoogleGenerativeAI(process.env.VITE_GEMINI_API_KEY);

const readFileAsBase64 = (file) => {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = () => resolve(reader.result.split(",")[1]);
    reader.onerror = reject;
    reader.readAsDataURL(file);
  });
};

const handleFileUpload = async (file, filetype) => {
  const base64Data = await readFileAsBase64(file);
  const imageParts = [
    {
      inlineData: {
        data: base64Data,
        mimeType: filetype,
      },
    },
  ];

  const model = genAI.getGenerativeModel({ model: "gemini-1.5-pro" });
  const prompt = "Analyze this medical image and provide insights.";

  const result = await model.generateContent([prompt, ...imageParts]);
  const response = await result.response;
  console.log(response.text());
};
```

## 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any improvements or bug fixes.

