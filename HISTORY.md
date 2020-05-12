# HISTORY

This history log references the repository releases which respect [semantic versioning](https://semver.org/).

## 3.0.1 (2020-05-12)

### Improvements

- Composer PHP requirement now accepts versions >=7.0.0 <8.0.0.
- HOWTO guide **CustomizableException** examples little improvements.

## 3.0.0 (2019-02-05)

### Improvements
- All [CustomizableException](src/CustomizableException/CustomizableException.php) message parts are now stored in
raw state.
    - The getters **getContext()**, **getDetails()** and **getMessageBase()** include **getL10N()** call.
    - **setContext()** doesn't call **getL10N()** anymore.
- :exclamation: Compatibility break :exclamation: The _$locale_ parameter is added to **getContext()**,
**getDetails()**, **getMessageBase()**, **getMessageFeStub()** and **getMessageFe()**.
- Return values type hints are removed for several methods in case if you want these methods to return raw
(untranslated) string or array of arguments: **getContext()**, **getDetails()**, **getMessageBase()**,
**getL10N()**, **getMessageFeStub()**, **getMessageDefault()**, **getMessageUnknown()**, **getMessageFe()**.
- ["_HOWTO_"](https://magicpush.github.io/enterprise-exception/) guide is updated to reflect these changes.
- Composer PHP requirement now accepts ~7.3 (no incompatibilities between 7.0 and 7.3).

## 2.3.0 (2018-11-11)

### Improvements

- [CustomizableException](src/CustomizableException/CustomizableException.php)::**getL10N()** first parameter type is
changed from 'string' to 'mixed' (for instance if you want to pass an array of arguments to your translation function).
    - The same thing is done for
[CustomizableException](src/CustomizableException/CustomizableException.php)::**setContext()** _$value_
    - The same thing is done for
      [CustomizableException](src/CustomizableException/CustomizableException.php)::**__construct()** _$details_
- ["_HOWTO_"](https://magicpush.github.io/enterprise-exception/) guide is updated to reflect these changes.

## 2.2.1 (2018-04-14)

### Fixes

- Composer PHP 7.2 version requirement (7.2 -> ^7.2)

## 2.2.0 (2018-03-17)

### New features

- ["_HOWTO for dummies and experienced_"](https://magicpush.github.io/enterprise-exception/) guide (english and russian
versions) powered by GitHub Pages.

### Fixes

- PHPDoc fixes.

### Other

- The classes for examples scripts are updated with namespaces - for better illustration.

## 2.1.0 (2018-02-23)

### New features

- [composer.json](composer.json) added for registering this library to **Packagist**.
- [GlobalException](src/GlobalException.php)::**getCodeClassMax()** public method
for the biggest class code public access.
- [Parser](src/CustomizableException/Parser.php)::**parse()** new option '_add_errors_' - to suppress validations errors
(like '_ignore_invalid_' option) and also add those errors messages to the output under '_\_\_errors_' key.

### Fixes

- [Parser](src/CustomizableException/Parser.php)::**parse()** crash when trying to filter
[GlobalException](src/GlobalException.php) descendants by class sections.

### Other

- [CustomizableException](src/CustomizableException/CustomizableException.php)::**getCodeFormatted()**
is moved to [GlobalException](src/GlobalException.php).
- [CustomizableException](src/CustomizableException/CustomizableException.php)::**getL10N()** parameter **$locale**
default value is changed to **null** (considering locale autodetection inside the method).
- [Parser](src/CustomizableException/Parser.php)::**loadClass()** doesn't check a class existence anymore.
Now it does absolutely nothing.
- [Parser](src/CustomizableException/Parser.php)::**parse()** has now an explicit check
if **$config_class_name** is loaded. This check can not be ignored.
- [Parser](src/CustomizableException/Parser.php)::**BASE_CLASS_NAME** is removed as redundant; **$config_class_name**
must be a subclass of [CustomizableException](src/CustomizableException/CustomizableException.php).

## 2.0 (2018-02-15)

The first open source release, initial public launch. All the code was redesigned and rewritten from scratch on my free
time.

The very first GitHub commit contains all things I wanted to implement for this exceptions management library. Future
updates are possible but not on a regular basis.

## 1.0 (2014-02-26)

The idea of global and customizable exceptions was implemented for the first time. It was used for a @sape-ru project
I continuously develop.

