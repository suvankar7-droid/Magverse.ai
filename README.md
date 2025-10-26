# Magverse AI - Premium AI Chat Platform

A futuristic AI chat platform that provides access to 6 different AI models through a single interface. Built with React, Vite, TailwindCSS, and OpenRouter API.

## 🌟 Features

### Auto Sign Up & Authentication
- ⚡ **Quick Sign Up (Auto)** - One-click instant account creation
- ✨ **Guest Mode** - Anonymous access without signup
- 📧 **Email Sign Up** - Traditional account creation
- 🎉 **Welcome Toast Notifications** - Friendly onboarding messages
- 🏷️ **Guest User Indicators** - Clear account type badges

### Plans & Credits System
- **Free Plan**: 5 credits per day (1 chat = 1 credit)
- **Pro Plan**: ₹299 for lifetime unlimited access
- Daily credit reset for free users
- Upgrade prompt when daily limit is reached

### 6 AI Models
1. **GPT-4 Turbo** (OpenAI)
2. **Claude 3 Opus** (Anthropic)
3. **Gemini Pro** (Google)
4. **Llama 3 70B** (Meta)
5. **Mistral Large** (Mistral AI)
6. **Command R+** (Cohere)

### UI/Interface
- 🎨 **Futuristic dark mode design** with gradient effects
- 📱 **Fully responsive** - works on mobile, tablet, and desktop
- 🎯 **Navbar**: Logo and login button
- 🚀 **Hero Section**: Call-to-action buttons and model showcase
- 💬 **Chat Interface**: 
  - Sidebar with AI model selection
  - Vertical stacked AI responses in card style
  - Chat history management
  - Real-time credit tracking
- 📺 **Demo video placeholder**
- 💎 **Upgrade page** with plan comparison

## 🚀 Getting Started

### Prerequisites
- Node.js 16+ installed
- OpenRouter API key (get it from [https://openrouter.ai/keys](https://openrouter.ai/keys))

### Installation

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Configure OpenRouter API**:
   - Open `src/services/aiService.js`
   - Replace `'sk-or-v1-YOUR_API_KEY_HERE'` with your actual OpenRouter API key:
   ```javascript
   const OPENROUTER_API_KEY = 'sk-or-v1-your-actual-key-here';
   ```

3. **Start the development server**:
   ```bash
   npm run dev
   ```

4. **Open your browser** and navigate to `http://localhost:3000`

## 📁 Project Structure

```
magverse-ai/
├── src/
│   ├── components/
│   │   ├── Navbar.jsx          # Navigation bar
│   │   ├── LoginModal.jsx      # Login/signup modal
│   │   ├── ChatSidebar.jsx     # Sidebar with models & history
│   │   └── ChatMessage.jsx     # Individual message component
│   ├── pages/
│   │   ├── HomePage.jsx        # Landing page with hero
│   │   ├── ChatPage.jsx        # Main chat interface
│   │   └── UpgradePage.jsx     # Pricing & upgrade page
│   ├── context/
│   │   └── AppContext.jsx      # Global state management
│   ├── services/
│   │   └── aiService.js        # OpenRouter API integration
│   ├── App.jsx                 # Main app component
│   ├── main.jsx                # Entry point
│   └── index.css               # Global styles
├── package.json
├── vite.config.js
├── tailwind.config.js
└── README.md
```

## 🎯 How It Works

### Authentication
- Simple email + name login (stored in localStorage)
- No backend required for demo purposes
- User session persists across page refreshes

### Credits System
- Free users: 5 credits per day, resets at midnight
- Pro users: Unlimited credits
- Credits are consumed per chat message
- Local storage tracks credit usage and daily reset

### Chat Flow
1. User logs in
2. Selects AI models from sidebar (1-6 models)
3. Types a message and sends
4. System checks credit availability
5. Message sent to selected AI models via OpenRouter API
6. Responses displayed in vertical cards
7. Chat history saved in localStorage

### Upgrade Flow
1. User clicks "Upgrade to Pro"
2. Sees plan comparison
3. Demo payment modal (simulated for now)
4. On "payment success", user upgraded to Pro
5. Unlimited credits granted

## 🔧 Configuration

### Changing AI Models
Edit `src/services/aiService.js` to add/remove models:
```javascript
const modelNames = {
  'openai/gpt-4-turbo': 'GPT-4 Turbo',
  // Add more models here
};
```

### Customizing Credits
Edit `src/context/AppContext.jsx`:
```javascript
const [credits, setCredits] = useState(5); // Change initial credits
```

### Styling
- Colors and theme: `tailwind.config.js`
- Global styles: `src/index.css`

## 🎨 Design Features

- **Glass morphism effects** for modern UI
- **Gradient text and backgrounds**
- **Smooth animations** and transitions
- **Custom scrollbars**
- **Responsive design** for all screen sizes
- **Dark mode** by default
- **Color-coded AI models** for easy identification

## 📝 Environment Variables (Optional)

For production, consider using environment variables:
```env
VITE_OPENROUTER_API_KEY=your_api_key_here
```

Then update `aiService.js`:
```javascript
const OPENROUTER_API_KEY = import.meta.env.VITE_OPENROUTER_API_KEY;
```

## 🚀 Building for Production

```bash
npm run build
```

This creates an optimized build in the `dist/` folder.

## 🔒 Security Notes

⚠️ **Important**: For production use:
1. Never expose API keys in client-side code
2. Implement a backend API to proxy OpenRouter requests
3. Use proper authentication (JWT, OAuth, etc.)
4. Implement actual payment processing (Razorpay, Stripe, etc.)
5. Add rate limiting and abuse prevention

## 🐛 Troubleshooting

### API Key Issues
- Make sure your OpenRouter API key is valid
- Check if you have credits in your OpenRouter account
- Verify the API key is correctly set in `aiService.js`

### CORS Issues
- OpenRouter API should work directly from browsers
- If issues persist, consider setting up a backend proxy

### Styling Issues
- Make sure TailwindCSS is properly installed
- Run `npm install` if dependencies are missing
- Clear browser cache and restart dev server

## 📚 Tech Stack

- **Frontend**: React 18
- **Build Tool**: Vite
- **Styling**: TailwindCSS
- **Routing**: React Router DOM
- **Icons**: Lucide React
- **HTTP Client**: Axios
- **AI API**: OpenRouter

## 🤝 Contributing

This is a demo project. Feel free to fork and customize for your needs!

## 📄 License

MIT License - feel free to use this project for personal or commercial purposes.

## 🎉 Credits

Built with ❤️ using modern web technologies.
Powered by OpenRouter API for multi-model AI access.

---

**Enjoy building with Magverse AI! 🚀**
