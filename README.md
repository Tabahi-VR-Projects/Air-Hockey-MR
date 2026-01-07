# 🏒 MR Air Hockey - Meta Quest 3/3S

A fully-featured **Mixed Reality Air Hockey** game for Meta Quest 3 and Quest 3S, built with Unity and powered by Meta XR SDK. Experience the thrill of air hockey with a virtual table seamlessly blended into your real-world environment!

## ✨ Features

### 🎮 Game Modes
- **Single Player**: Play against AI with adjustable difficulty (Easy/Medium/Hard)
- **Online Multiplayer**: Challenge friends remotely using Photon Fusion 2 networking
- **Room Code System**: Easy matchmaking with 4-digit room codes

### 🥽 Mixed Reality
- **Passthrough Integration**: Full MR experience with Meta Quest 3/3S passthrough
- **World-Space UI**: Intuitive menus and controls floating in your space
- **Hand/Controller Tracking**: Natural paddle control using Quest controllers
- **Comfortable Table Positioning**: Adjustable height and distance for optimal gameplay

### 🎯 Gameplay Features
- Realistic physics-based puck and paddle interactions
- Score tracking with customizable win conditions (default: first to 7)
- Smooth 72+ FPS performance on Quest 3S

### 🌐 Networking (Multiplayer)
- **Photon Fusion 2** for reliable real-time multiplayer
- Host/Client architecture with automatic room creation
- Network-synchronized physics and game state
- Voice chat support (Photon Voice integration)
- Disconnection handling with automatic win assignment

---

## 🛠️ Technology Stack

| Component | Technology |
|-----------|------------|
| **Game Engine** | Unity 2022.3.52f1 LTS |
| **VR Framework** | Meta XR SDK 83.0.1 |
| **Rendering Pipeline** | URP (Universal Render Pipeline) |
| **Networking** | Photon Fusion 2.0.x |
| **Platform** | Meta Quest 3 / Quest 3S |
| **Build Target** | Android (Quest OS) |

---

## 📋 Requirements

### Development Requirements
- **Unity**: 2022.3 LTS (2022.3.52f1 recommended)
- **Meta XR SDK**: Version 83.0.1
- **Photon Fusion**: Version 2.0+

### Runtime Requirements
- **Device**: Meta Quest 3 or Quest 3S
- **OS**: Latest Quest firmware
- **Space**: 2m x 2m play area recommended
- **Internet**: Required for multiplayer mode

---

## 🚀 Getting Started

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/MR-AirHockey-Quest3.git
cd MR-AirHockey-Quest3
```

### 2. Open in Unity
- Open **Unity Hub**
- Click **Open** → Select project folder
- Unity will import all assets (may take 5-10 minutes)

### 3. Install Dependencies
Required packages will auto-import. If not:
- **Meta XR SDK**: Import from Asset Store
- **Photon Fusion**: Import from Asset Store
- **Photon Voice** (optional): Import from Asset Store

### 4. Configure Photon
1. Create account at [Photon Engine](https://www.photonengine.com/)
2. Create **Fusion** app and copy App ID
3. In Unity: `Assets/Photon/Fusion/Resources/PhotonAppSettings`
4. Paste App ID in **App Id Fusion** field

### 5. Build Settings
- **File → Build Settings**
- **Platform**: Android
- **Texture Compression**: ASTC
- **Minimum API Level**: Android 10 (API 29)
- **Target API Level**: Android 13+ (API 33)
- **Scripting Backend**: IL2CPP
- **Target Architectures**: ARM64 only

### 6. Enable Developer Mode
- Install **Meta Quest mobile app**
- Connect your Quest 3/3S
- Enable **Developer Mode** in app settings
- Approve USB debugging on headset

### 7. Build and Run
- Connect Quest via USB-C
- **File → Build Settings → Build And Run**
- Game will install and launch on your headset

---

## 🎮 How to Play

### Single Player Mode
1. Launch game on Quest 3/3S
2. Select **PLAY SOLO** from main menu
3. Use right controller to control paddle
4. Score goals by hitting puck into opponent's goal
5. First to 7 points wins!

### Multiplayer Mode
1. Launch game on both devices
2. **Player 1**: Select **PLAY ONLINE → CREATE ROOM**
   - Note the 4-digit room code
3. **Player 2**: Select **PLAY ONLINE → JOIN ROOM**
   - Enter the room code
4. Game starts automatically when both players connect
5. Enjoy real-time online air hockey!

### Controls
- **Right Controller**: Move to control paddle
- **Primary Index Trigger**: Interact with UI buttons
- **Paddle Movement**: Automatically tracked to controller position

---

## 📁 Project Structure
```
Assets/
├── Scenes/
│   ├── MainMenu.unity              # Main menu with mode selection
│   ├── AirHockey_Main.unity        # Single-player game scene
│   ├── MultiplayerLobby.unity      # Multiplayer lobby UI
│   └── AirHockey_Multiplayer.unity # Multiplayer game scene
├── Scripts/
│   ├── GameManager.cs              # Single-player game logic
│   ├── NetworkGameManager.cs       # Multiplayer game logic
│   ├── NetworkManager.cs           # Photon connection handling
│   ├── LobbyManager.cs             # Multiplayer lobby UI
│   ├── PlayerPaddleController.cs   # Single-player paddle control
│   ├── NetworkPaddleController.cs  # Multiplayer paddle control
│   ├── AIPaddleController.cs       # AI opponent logic
│   ├── PuckCollision.cs            # Single-player puck physics
│   ├── NetworkPuckCollision.cs     # Multiplayer puck physics
│   └── GoalTrigger.cs              # Goal detection
├── Prefabs/
│   ├── Network/
│   │   ├── NetworkRunnerPrefab     # Photon Fusion runner
│   │   ├── Puck_Network            # Networked puck prefab
│   │   └── Paddle_Network          # Networked paddle prefab
│   └── ...
├── Materials/                       # Game materials
├── Audio/                          # Sound effects
└── Photon/                         # Photon SDK files
```

---

## 🎨 Customization

### Adjust AI Difficulty
Edit `AIPaddleController.cs`:
```csharp
public enum AIDifficulty { Easy, Medium, Hard }
[SerializeField] private AIDifficulty difficulty = AIDifficulty.Medium;
```

### Change Table Position
Edit in GameManager or NetworkGameManager:
```csharp
[SerializeField] private Vector3 tableCenter = new Vector3(0, 0.9f, 1.5f);
```

### Modify Score Limit
```csharp
[SerializeField] private int maxScore = 7; // First to 7 wins
```

### Customize Materials/Colors
- Navigate to `Assets/Materials/`
- Edit paddle, puck, and table materials
- Adjust colors, emission, and effects

---

## 🐛 Known Issues

- **Puck physics**: Occasionally puck may clip through walls at very high speeds (velocity clamping implemented)
- **Network latency**: ~50-100ms delay in opponent paddle movement (normal for Photon)
- **Passthrough performance**: Slight FPS drop on Quest 3S when many objects visible (optimized to 72+ FPS)

---

## 🔮 Future Enhancements

- [ ] Hand tracking support (no controller mode)
- [ ] Tournament mode with bracket system
- [ ] Customizable table themes and skins
- [ ] Power-ups (speed boost, larger paddle, etc.)
- [ ] Leaderboards and statistics tracking
- [ ] Spectator mode for multiplayer matches
- [ ] Local multiplayer (shared space, same room)
- [ ] Haptic feedback improvements
- [ ] Advanced AI with machine learning

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 🙏 Acknowledgments

- **Meta** for the Quest 3/3S platform and XR SDK
- **Photon Engine** for networking solution
- **Unity Technologies** for the game engine
- Claude (Anthropic) for development assistance and guidance
- The VR/MR development community for invaluable resources

---

## 📧 Contact

**Muhammad Abdullah** - 1005abdullah.lecole@gmail.com

**Omer Abdullah** - omerabdullah626@gmail.com



**Made with ❤️ for the Meta Quest community**
