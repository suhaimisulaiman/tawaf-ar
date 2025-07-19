# Tawaf AR Trainer

A web-based Augmented Reality training tool for learning the Tawaf ritual during Hajj pilgrimage.

## Features

- **AR Training**: Point your camera at a Kaaba image to see 3D AR content
- **7-Round Guidance**: Step-by-step instructions for completing Tawaf
- **Multi-language Support**: English, Arabic, and Bahasa Melayu
- **Audio Guidance**: Prayer recitations and instructions
- **Progress Tracking**: Visual progress bar and round counter
- **Mobile Optimized**: Designed for smartphones and tablets

## Quick Start

### Local Development
```bash
# Start local server
python3 -m http.server 8000

# Or using npm
npm install
npm run serve
```

### Deploy to Web
1. **Netlify**: Drag and drop this folder to [netlify.com](https://netlify.com)
2. **Vercel**: Push to GitHub and import to [vercel.com](https://vercel.com)
3. **GitHub Pages**: Push to GitHub and enable Pages in settings

## How to Use

1. **Access the app** on your mobile device
2. **Allow camera permissions** when prompted
3. **Point camera** at a Kaaba image or use the "Test Tracking" button
4. **Follow the AR guidance** to complete the 7 rounds of Tawaf
5. **Listen to audio instructions** and prayers

## Technical Details

- **AR.js**: Web-based AR library
- **A-Frame**: 3D web framework
- **Hiro Marker**: AR tracking marker (included)
- **Responsive Design**: Works on all mobile devices

## Requirements

- Modern mobile browser (Chrome, Safari, Firefox)
- Camera access
- HTTPS connection (for AR functionality)
- Good lighting for marker detection

## Testing

- Use the "Test Tracking" button to simulate AR detection
- Print the hiro marker for real AR testing
- Test on actual mobile devices (not desktop)

## License

MIT License - Feel free to use and modify for educational purposes. 