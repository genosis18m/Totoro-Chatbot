# Totoro-Chatbot
# Totoro Chatbot - Project Documentation  

## 📖 Project Overview  
A conversational AI interface leveraging Google's Gemini 1.5 Flash model for multimodal interactions (text + images). Features real-time chat functionality with dynamic UI updates and responsive design.  

---

## 🛠️ Technology Stack  

### Core Technologies  
| Component | Technologies |  
|-----------|--------------|  
| **Frontend** | HTML5, CSS3 (Flexbox, Media Queries), Vanilla JavaScript |  
| **AI Backend** | Gemini 1.5 Flash API (RESTful integration) |  
| **Data Handling** | Base64 image encoding, JSON payloads |  

### Key Libraries/APIs  
- **Generative Language API**: `gemini-1.5-flash` model endpoint  
- **Browser APIs**: Fetch API, DOM Manipulation, FileReader  

---

## 🧠 Functional Architecture  

### System Components  
1. **UI Layer** (`index.html`)  
   - Chat container with message threading  
   - Multimodal input system (text + file upload)  
   - Responsive breakpoints for mobile (<600px)  

2. **Presentation Layer** (`style.css`)  
   - CSS Variables-free atomic design  
   - Advanced positioning:  
     - Relative/absolute positioning for chat bubbles  
     - Flexbox-based message alignment  
   - Visual effects:  
     - Drop shadows (`filter: drop-shadow()`)  
     - Smooth transitions (button hover states)  

3. **Logic Layer** (`script.js`)  
   ```javascript  
   // Core workflow
   async function generateResponse() {
     // 1. Construct multipart payload
     const payload = {
       contents: [{
         parts: [
           {text: user.message},
           ...(user.file.data ? [{inline_data: user.file}] : [])
         ]
       }]
     };

     // 2. API call with error handling
     const response = await fetch(Api_Url, {
       method: "POST",
       headers: {'Content-Type': 'application/json'},
       body: JSON.stringify(payload)
     });

     // 3. Response processing
     const data = await response.json();
     return data.candidates[0].content.parts[0].text;
   }
   ```

---

## 🔑 Technical Highlights  

### Advanced Features  
1. **Multimodal Input Processing**  
   - Image-to-base64 conversion workflow  
   - MIME type validation via `file.type`  

2. **Performance Optimizations**  
   - Non-blocking async/await pattern  
   - DOM recycling (dynamic element creation vs innerHTML)  

3. **Security Measures**  
   - API key scoping to Gemini endpoints  
   - Input sanitization via regex:  
     ```javascript 
     .replace(/\*\*(.*?)\*\*/g,"$1").trim()
     ```

---

## 📂 File Structure  
```
project-root/  
├── index.html          # Entry point  
├── style.css           # Presentation rules  
└── script.js           # Application logic  
```

---

## 🚀 Setup Guide  

1. **Requirements**  
   - Modern browser (Chrome 120+)  
   - Google API key with Gemini permissions  

2. **Configuration**  
   ```javascript
   const Api_Url = "https://generativelanguage.googleapis.com/...key=YOUR_API_KEY";
   ```
---

## 📝 License & Attribution  
- **Author**: Genosis   
- **License**: Mohit
- **Acknowledgments**: Google DeepMind for Gemini API  

## I used perplexity for this readme file :)
