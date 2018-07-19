# bintray gradle scripts

Publish your android library to [bintray](https://bintray.com/) (jcenter).

## Setup

### 1. add required plugins to the project's classpath

In you project's `build.gradle`, add

```groovy
classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7.3'
classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5'
```

inside the buildscript > dependencies:

```groovy
buildscript {
    
    repositories {
        google()
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.1.3'
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7.3' // this line
        classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5' // and this 
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}
```

### 2. set your bintray user keys _`locally`_

In your project's `local.properties`:

```groovy
bintray.user= # your user name
bintray.apikey= # your api key
bintray.gpg.password= # your password
```

### 3. define the library-specific properties

In your library module's `build.gradle`, add:

```groovy
ext {
    bintrayRepo = 'Hong'
    bintrayName = 'checkerboarddrawable'

    publishedGroupId = 'com.github.duanhong169'
    artifact = 'checkerboarddrawable'

    libraryDescription = 'A custom Drawable to use as background which embody "transparent", AKA checkerboard grid.'
    libraryVersion = '1.0.0'
    
    gitUrl = 'https://github.com/duanhong169/CheckerboardDrawable.git'
    siteUrl = 'https://github.com/duanhong169/CheckerboardDrawable'

    licenseName = 'Apache License 2.0'
    licenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
    allLicenses = ["Apache-2.0"]
}
```

> Edit the values to yours as needed.

### 4. apply the script:

In your library module's `build.gradle`, add:

```groovy
apply from: 'https://raw.githubusercontent.com/duanhong169/bintray-gradle/master/bintray.gradle'
```

Or you can copy the `bintray.gradle` file into your library module's root directory, and apply from it by add:

```groovy
apply from: 'bintray.gradle'
```

## Publish!

Just run:

```shell
./gradlew bintrayUpload
```

in your project root path.

## Example

See the project [`CheckerboardDrawable`](https://github.com/duanhong169/CheckerboardDrawable) for example.