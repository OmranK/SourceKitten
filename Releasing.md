# Releasing SourceKitten

For SourceKitten contributors, follow these steps to cut a release:

1. Update version number in the following files:
    * `Source/sourcekitten/Supporting Files/Info.plist`
    * `Source/SourceKittenFramework/Supporting Files/Info.plist`
2. Come up with a witty feline themed release name. Past names include:
    * Objective-Cat
    * Cat-astrophic
    * SourceClangKitLibKitten
    * Grumpy Cat
3. Update the first header in `CHANGELOG.md` to the new version number & release
   name.
4. Commit & push to the `master` branch.
5. Tag: `git tag -a 0.6.2 -m "0.6.2: Objective-Cat"; git push --tags`
6. Make sure you have the latest stable Xcode version installed or symlinked
   under `/Applications/Xcode.app` and `xcode-select`ed.
7. Create the pkg installer: `make package`
8. Create the Carthage framework zip:
     * `mkdir -p Carthage/Build/Mac`
     * `mv /tmp/SourceKitten.dst/usr/local/Frameworks/SourceKittenFramework.framework Carthage/Build/Mac`
     * `carthage archive SourceKittenFramework`
9. Create a GitHub release: https://github.com/realm/SourceKitten/releases/new
    * Specify the tag you just pushed from the dropdown.
    * Set the release title to the new version number & release name.
    * Add the changelog section to the release description text box.
    * Upload the pkg installer and Carthage zip you just built to the GitHub
      release binaries.
    * Click "Publish release"
10. File a PR towards Homebrew bumping the `tag`, `revision` & Xcode version
    dependency if necessary.
    See [homebrew#45651](https://github.com/Homebrew/homebrew/pull/45651) as an
    example.