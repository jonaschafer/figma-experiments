# PDX Campsite Reporter

A conversational mobile-first web app that makes reporting homeless campsites to the City of Portland faster and easier.

## 🎯 The Problem

Portland's official campsite reporting form has multiple screens, dropdowns, and text fields that are tedious to fill out on mobile - especially when you're standing on the street looking at a campsite.

## ✨ The Solution

A chat-based interface that:
- Asks simple questions one at a time
- Offers quick-tap buttons for common answers
- Supports voice-to-text input
- Takes ~60 seconds to complete
- Pre-fills Portland's official form for one-tap submission

## 🚀 Demo

**Live:** [figma-experiments.vercel.app/campsite-reporter](https://figma-experiments.vercel.app/campsite-reporter)

**Best viewed on mobile** (that's the whole point!)

## 🛠️ Technical Details

### Stack
- Pure HTML/CSS/JavaScript
- No frameworks or dependencies
- Uses Web Speech API for voice input
- Mobile-first responsive design

### Features
- ✅ Conversational UI with typing indicators
- ✅ Quick-response buttons
- ✅ Voice-to-text input (works in Chrome/Safari)
- ✅ Real-time validation
- ✅ Summary review before submission
- ✅ Restart functionality for multiple reports

### Browser Support
- ✅ iOS Safari (iPhone)
- ✅ Chrome (Android)
- ✅ Desktop browsers (for testing)
- ⚠️ Voice input requires HTTPS and modern browser

## 📱 How It Works

1. User opens the app on their phone
2. Bot asks 6 simple questions:
   - Where is the campsite?
   - How many tents?
   - Any vehicles?
   - When did you notice it?
   - Additional notes? (optional)
   - Email for follow-up? (optional)
3. User answers via text, voice, or quick buttons
4. App shows summary
5. **Opens user's email app with pre-filled email to reportpdx@portlandoregon.gov**
6. User reviews and hits send - done in 10 seconds!

## 🎯 Why Email Instead of Web Form?

Portland accepts campsite reports via:
- ✅ Email: reportpdx@portlandoregon.gov (what we use - reliable & automatable)
- Web form (multiple pages, can't be pre-filled)
- PDX Reporter website (similar limitations)
- Phone: 503-823-4000

Email is the **only method that can be fully automated** - the app opens your email client with everything pre-filled, you just review and send.

## 🎨 Design Decisions

**Why conversational?**
- Natural interaction pattern
- One question at a time reduces cognitive load
- Works well while walking/standing outside

**Why big buttons?**
- Easy to tap with gloves/cold hands
- Faster than typing
- Reduces errors

**Why voice input?**
- Hands-free operation
- Faster for addresses
- Better UX when reporting from the street

## 🔮 Future Enhancements

- [ ] GPS auto-location
- [ ] Photo upload
- [ ] Save draft reports
- [ ] Show map of reported sites
- [ ] Spanish language support
- [ ] Offline support (PWA)

## 🏗️ For Engineers

This prototype could be adapted for:
- Other government forms
- Customer feedback collection
- Incident reporting
- Field data collection
- Any tedious form that needs mobile simplification

### Key Patterns Used
```javascript
// Conversational state management
let conversationState = {
    step: 0,
    data: {}
};

// Question flow
const questions = [
    { question: "...", key: 'fieldName', options: [...] }
];

// Progressive disclosure
function askQuestion() {
    // Show one question at a time
    // Add buttons for common responses
    // Support free text input
}
```

### Reusable Components
- Typing indicator animation
- Message bubble styling
- Voice input integration
- Button group layout

## 📊 Impact

**Goal:** Make neighborhood reporting 10x easier

**Metrics to track:**
- Time to complete (target: <60 seconds)
- Completion rate
- Voice input usage
- Mobile vs desktop traffic

## 🤝 Contributing

This is a community tool. Ideas for improvement:
1. Test it in your neighborhood
2. Report bugs/suggestions
3. Fork and adapt for other forms
4. Share with neighbors

## 📄 License

MIT - Feel free to use for your own city/community!

---

Built in Portland, for Portland 🌲
