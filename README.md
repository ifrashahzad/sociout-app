# Sociout

Welcome to Sociout, a social media app that connects people through photo and video sharing, stories, and direct messaging. Inspired by Instagram, Sociout lets you capture moments, discover new content, and stay connected with friends and family.

## Features

- **Photo and Video Sharing**: Share your moments through photos and videos.
- **Stories**: Post stories that disappear after 24 hours.
- **Direct Messaging**: Send private messages to friends and family.
- **Discover**: Find new content and follow new people.

## Getting Started

These instructions will help you set up and run the Sociout project on your local machine for development and testing purposes.

### Prerequisites

- [Flutter SDK](https://flutter.dev/docs/get-started/install)
- [Android Studio](https://developer.android.com/studio) or [Visual Studio Code](https://code.visualstudio.com/)
- A Firebase project with Android app registered and `google-services.json` file downloaded

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/sociout.git
   cd sociout
   
2. **Install dependencies**
flutter pub get

4. **Set up Firebase**
Place the google-services.json file in the android/app directory.

5. **Run the app**
flutter run

**Firebase Integration**
Sociout uses Firebase for the following services:

-Authentication: User login and registration
-Cloud Firestore: Real-time database to store user data and posts
-Firebase Storage: Store photos and videos
-Firebase Analytics: Track user interactions and events

**Adding Firebase to your Flutter project**
1. **Project-level build.gradle**
buildscript {
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:7.1.0'
        classpath 'com.google.gms:google-services:4.3.10'
    }
}

allprojects {
    repositories {
        google()
        mavenCentral()
    }
}
2. **App-level build.gradle**
apply plugin: 'com.android.application'
apply plugin: 'com.google.gms.google-services'

android {
    compileSdkVersion 31

    defaultConfig {
        applicationId "com.example.sociout"
        minSdkVersion 21
        targetSdkVersion 31
        versionCode 1
        versionName "1.0"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    implementation platform('com.google.firebase:firebase-bom:31.2.0')

    implementation 'com.google.firebase:firebase-analytics'
    implementation 'com.google.firebase:firebase-auth'
    implementation 'com.google.firebase:firebase-firestore'
    implementation 'com.google.firebase:firebase-storage'
}
3. **Initialize Firebase in your Flutter app**
import 'package:firebase_core/firebase_core.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(SocioutApp());
}




