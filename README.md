# Scalable Flutter App Starter


# Docs

## Code Architecture

The code architecture is based on
[flutter_bloc architecture proposal](https://bloclibrary.dev/#/architecture).

There are 4 layers:

1. UI (Flutter Widgets)
2. BLoC (stateful business logic)
3. Repository (high-level API)
4. Provider (low-level implementation)

And there's only 1 communication rule that we must follow:

_**The layer can only call the one layer below it.**_

That means that:

- UI can only call BLoC
- BLoC can only call Repository
- Repository can only call Provider
- Provider can only call external services (Firebase, HTTP, etc.)

And we avoid same-layer communication (as it creates interdependencies):

- `UserRepository` calling `AuthRepository` is _**not**_ allowed.
- `UserCubit` calling `UserRepository` and `AuthRepository` is allowed.

## Styling

Styling is based on [Google's Material Design](https://material.io/design).

App-wide styling is defined in `core/app/style.dart` and is easy to update.

Here's a quick tip on custom Widget params. There are 2 Widget param types:

- data (user, title, ...)
- style (colors, paddings, ...)

Our custom Widgets should only hava data params.

And the style should be done app-wide (in `style.dart`).

That way all of our UI is consistent and easy to update.

## Google Fonts

To change the font:

1. Go to [Google Fonts](https://fonts.google.com/) and select a font.
2. Download the font files.
3. Add the font files to `assets/fonts` (remove the old ones).
4. Update `style.dart` with the new font (i.e. `return GoogleFonts.rubikTextTheme(textTheme)`).

## Useful GitHub Pull Request Settings

I've found that turning on these 2 settings in GitHub repo settings helps a lot:

1. `Always suggest updating pull request branches`
2. `Automatically delete head branches`

# FAQ

## Why bloc and not X?

While GetX, Provider, Riverpod, MobX, Redux, etc. are all great solutions,
most of them are too forgiving. They allow us to access and change state globally.

Whereas [flutter_bloc](https://bloclibrary.dev/) forces us to have `BuildContext`
in order to access and change the state. The stricter the rules, the harder it is to make mistakes.

And flutter_bloc has a great [architecture proposal](https://bloclibrary.dev/#/architecture) that
scales well.

## Who is Scalable Flutter App for?

Scalable Flutter App is for developers, agencies, and founders who want to:

- build scalable Flutter apps
- save weeks of development time
- learn best practices

## Where to learn Flutter basics?

I can only recommend what I've used myself:

- [Flutter Codelabs](https://docs.flutter.dev/codelabs)
- [Flutter YouTube](https://www.youtube.com/channel/UCwXdFgeE9KYzlDdR7TG9cMw)
- [Effective Dart](https://dart.dev/guides/language/effective-dart)
- and just keep building apps and getting better with each one :)

## What if I want more?

If you want Firebase integration, notifications, in-app purchases and more,
you can get the Pro version here ($200-off discount lasts until end of October):

[Get Your Scalable Flutter App PRO for $47 ($200 OFF)](https://gradoid.lemonsqueezy.com/checkout/buy/b8fff0c2-d8ce-4af2-ac33-b675ef858c5c?checkout%5Bdiscount_code%5D=APP200)

# Resources

Build your app icon in minutes (free): [Icon Kitchen](https://icon.kitchen/)

CI/CD for mobile apps (free & paid): [Codemagic](https://codemagic.io/)

Want me to launch your MVP in 4 weeks (premium)?
[Go to App Launch Program](https://applaunchprogram.com/)

Need a Flutter Expert (paid)? [Go to Flutter Devs Board](https://flutterdevsboard.com/)


