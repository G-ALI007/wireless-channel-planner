# Wireless Channel Planner 📡

[العربية](#النسخة-العربية) | [English](#english-version)

---

## English Version

A comprehensive C++ library for planning and optimizing wireless channels and frequencies in WiFi networks. This library helps network engineers design efficient wireless networks by managing channel allocation, avoiding interference, and optimizing channel distribution across access points.

### ✨ Features

- **Multi-Band Support**: 2.4 GHz and 5 GHz frequency bands
- **WiFi Standards**: Support for 802.11b/g/n/ac/ax (WiFi 4/5/6)
- **Channel Bandwidth**: 20/40/80/160 MHz channel widths
- **Interference Detection**: Detect and avoid channel overlap
- **Optimal Channel Selection**: Find the best channel for new access points
- **Geographic Planning**: Distance-based interference calculation
- **Network Analysis**: Channel utilization statistics and reporting
- **Easy Integration**: Simple, clean C++ API

### 🚀 Quick Start

#### Prerequisites

- C++11 or later
- CMake 3.10 or later
- Standard C++ compiler (GCC, Clang, or MSVC)

#### Building the Library

```bash
# Clone the repository
git clone https://github.com/G-ALI007/wireless-channel-planner.git
cd wireless-channel-planner

# Create build directory
mkdir build && cd build

# Configure and build
cmake ..
make

# Run the example
./channel_planner_example
```

### 📖 Usage Examples

#### Basic Channel Planning

```cpp
#include "channel_planner.h"
using namespace WirelessPlanner;

// Create a channel planner
ChannelPlanner planner(WiFiStandard::IEEE_802_11ac);

// Get non-overlapping channels for 2.4 GHz
auto channels = planner.getNonOverlappingChannels24GHz();
for (const auto& ch : channels) {
    std::cout << "Channel " << ch.number << ": " 
              << ch.centerFrequency << " MHz" << std::endl;
}
```

#### Adding Access Points

```cpp
// Create a channel
Channel ch1(1, 2412.0, FrequencyBand::BAND_2_4_GHZ, ChannelBandwidth::BW_20_MHZ);

// Create an access point
AccessPoint ap("AP-Office", 52.3676, 4.9041, ch1, 20.0);

// Add to network
planner.addAccessPoint(ap);
```

#### Finding Optimal Channel

```cpp
// Find best channel for a new AP location
Channel optimal = planner.findOptimalChannel(
    52.3696,  // latitude
    4.9061,   // longitude
    FrequencyBand::BAND_2_4_GHZ,
    ChannelBandwidth::BW_20_MHZ
);

std::cout << "Optimal channel: " << optimal.number << std::endl;
```

#### Checking Channel Overlap

```cpp
Channel ch1(1, 2412.0, FrequencyBand::BAND_2_4_GHZ, ChannelBandwidth::BW_20_MHZ);
Channel ch6(6, 2437.0, FrequencyBand::BAND_2_4_GHZ, ChannelBandwidth::BW_20_MHZ);

bool overlap = planner.doChannelsOverlap(ch1, ch6);
std::cout << "Channels overlap: " << (overlap ? "Yes" : "No") << std::endl;
```

### 📚 API Reference

#### ChannelPlanner Class

Main class for channel planning and management.

**Constructor:**
```cpp
ChannelPlanner(WiFiStandard standard = WiFiStandard::IEEE_802_11n)
```

**Key Methods:**
- `getAvailableChannels()` - Get all available channels for a band
- `getNonOverlappingChannels24GHz()` - Get non-overlapping 2.4 GHz channels
- `findOptimalChannel()` - Find best channel for new AP
- `addAccessPoint()` - Add AP to network
- `removeAccessPoint()` - Remove AP from network
- `calculateInterferenceScore()` - Calculate interference for a channel
- `doChannelsOverlap()` - Check if two channels overlap
- `getChannelUtilization()` - Get channel usage statistics
- `generateReport()` - Generate network report

#### ChannelUtils Class

Utility functions for channel and frequency conversions.

**Static Methods:**
- `channelToFrequency()` - Convert channel number to frequency
- `frequencyToChannel()` - Convert frequency to channel number
- `getStandardName()` - Get WiFi standard name
- `getBandName()` - Get frequency band name

### 🏗️ Project Structure

```
wireless-channel-planner/
├── include/
│   └── channel_planner.h      # Main header file
├── src/
│   └── channel_planner.cpp    # Implementation
├── examples/
│   └── example.cpp            # Usage examples
├── tests/                     # Unit tests (optional)
├── CMakeLists.txt            # Build configuration
├── README.md                 # This file
├── LICENSE                   # MIT License
└── .gitignore               # Git ignore file
```

### 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### 👨‍💻 Author

ghader ali - Telecommunications Engineer

### 🙏 Acknowledgments

- WiFi standards documentation (IEEE 802.11)
- Network planning best practices
- Open source community

---

## النسخة العربية

مكتبة C++ شاملة لتخطيط وتحسين القنوات والترددات اللاسلكية في شبكات WiFi. تساعد هذه المكتبة مهندسي الشبكات على تصميم شبكات لاسلكية فعالة من خلال إدارة توزيع القنوات، تجنب التداخل، وتحسين توزيع القنوات عبر نقاط الوصول.

### ✨ المميزات

- **دعم متعدد النطاقات**: نطاقات 2.4 GHz و 5 GHz
- **معايير WiFi**: دعم 802.11b/g/n/ac/ax (WiFi 4/5/6)
- **عرض النطاق**: 20/40/80/160 ميجاهرتز
- **كشف التداخل**: اكتشاف وتجنب تداخل القنوات
- **اختيار القناة الأمثل**: إيجاد أفضل قناة لنقاط وصول جديدة
- **التخطيط الجغرافي**: حساب التداخل بناءً على المسافة
- **تحليل الشبكة**: إحصائيات استخدام القنوات والتقارير
- **سهولة التكامل**: واجهة برمجية بسيطة ونظيفة

### 🚀 البدء السريع

#### المتطلبات

- C++11 أو أحدث
- CMake 3.10 أو أحدث
- مترجم C++ قياسي (GCC, Clang, أو MSVC)

#### بناء المكتبة

```bash
# استنساخ المستودع
git clone https://github.com/G-ALI007/wireless-channel-planner.git
cd wireless-channel-planner

# إنشاء مجلد البناء
mkdir build && cd build

# التكوين والبناء
cmake ..
make

# تشغيل المثال
./channel_planner_example
```

### 📖 أمثلة الاستخدام

#### تخطيط القنوات الأساسي

```cpp
#include "channel_planner.h"
using namespace WirelessPlanner;

// إنشاء مخطط قنوات
ChannelPlanner planner(WiFiStandard::IEEE_802_11ac);

// الحصول على القنوات غير المتداخلة لـ 2.4 GHz
auto channels = planner.getNonOverlappingChannels24GHz();
for (const auto& ch : channels) {
    std::cout << "القناة " << ch.number << ": " 
              << ch.centerFrequency << " ميجاهرتز" << std::endl;
}
```

#### إضافة نقاط الوصول

```cpp
// إنشاء قناة
Channel ch1(1, 2412.0, FrequencyBand::BAND_2_4_GHZ, ChannelBandwidth::BW_20_MHZ);

// إنشاء نقطة وصول
AccessPoint ap("AP-Office", 52.3676, 4.9041, ch1, 20.0);

// إضافة للشبكة
planner.addAccessPoint(ap);
```

#### إيجاد القناة المثلى

```cpp
// إيجاد أفضل قناة لموقع نقطة وصول جديدة
Channel optimal = planner.findOptimalChannel(
    52.3696,  // خط العرض
    4.9061,   // خط الطول
    FrequencyBand::BAND_2_4_GHZ,
    ChannelBandwidth::BW_20_MHZ
);

std::cout << "القناة المثلى: " << optimal.number << std::endl;
```

### 📚 مرجع API

راجع النسخة الإنجليزية أعلاه للحصول على تفاصيل كاملة عن API.

### 🤝 المساهمة

المساهمات مرحب بها! لا تتردد في تقديم Pull Request. للتغييرات الكبيرة، يرجى فتح issue أولاً لمناقشة ما تريد تغييره.

### 📝 الترخيص

هذا المشروع مرخص بموجب ترخيص MIT - راجع ملف [LICENSE](LICENSE) للتفاصيل.

### 👨‍💻 المؤلف

اسمك - مهندس اتصالات

---

**Star ⭐ this repository if you find it helpful!**

**ضع نجمة ⭐ للمستودع إذا وجدته مفيداً!**
