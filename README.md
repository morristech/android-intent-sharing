# Sharing sounds to SoundCloud via intents

This is a small sample app to demonstrate how you could integrate SoundCloud in your
own Android application. You can record some audio and then upload it to
SoundCloud with the official Android app (which must be installed).

If it is not installed the user will be prompted to install it.

## How sharing works

The integration works with the standard [Android intent model][]:


    File myAudiofile = new File("/path/to/audio.mp3");
    Intent intent = new Intent("com.soundcloud.android.SHARE")
        .putExtra(Intent.EXTRA_STREAM, Uri.fromFile(myAudiofile))
        .putExtra("com.soundcloud.android.extra.title", "Demo")
        .putExtra("com.soundcloud.android.extra.description", "Testing");

    try {
       startActivityForResult(intent, 0);
    } catch (ActivityNotFoundException e) {
      // SoundCloud Android app not installed, show a dialog etc.
    }



[Android intent model]: http://developer.android.com/reference/android/content/Intent.html