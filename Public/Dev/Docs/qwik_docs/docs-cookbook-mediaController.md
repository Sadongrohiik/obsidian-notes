# https://qwik.dev/docs/cookbook/mediaController/

[Original link](https://qwik.dev/docs/cookbook/mediaController/)

# Media Controller

Developing for a diverse range of browsers and devices often introduces unique challenges. One of the most notable challenges is ensuring consistent media playback, particularly on Apple's iOS devices.

## iOS Media Playback Restrictions Explained

Apple's iOS has established specific rules for audio and video playback to enhance user experience and manage data consumption:

## Deciphering the iOS Playback Challenge

At the heart of the iOS challenge is the system's insistence on user-initiated media playback. For instance, starting a video must result directly from a user action, like a tap. However, asynchronous event handlers, such as onClick$ (QRL), can create a disconnect between the user's action and the playback command. This often results in iOS blocking playback on the first tap, requiring a second, non-intuitive tap.

## The playsinline Attribute

On iOS devices, especially iPhones, videos automatically play in fullscreen mode unless the playsinline attribute is present on the <video> tag. This attribute ensures that videos play within their designated container, providing a consistent experience across different devices and platforms. While primarily intended for iOS, including playsinline is harmless on other platforms and ensures broader compatibility.

## Crafting a Universal Playback Solution

To achieve consistent media playback across various browsers and devices, a holistic approach is essential. This guide presents a solution that addresses the nuances of different platforms. To ensure immediate playback upon user interaction, the .play() method should be invoked synchronously. This can be accomplished by directly attaching the click handler within the useVisibleTask$ function.

Below, you'll find a prototype of an audio and video controller, tailored to provide a consistent user experience across multiple platforms.

Universal media controller code compatible with iOS devices looks like this:

```
import {
  component$,
  useSignal,
  useStylesScoped$,
  useVisibleTask$,
} from '@builder.io/qwik';
import { useLocation } from '@builder.io/qwik-city';
 
const AUDIO_SRC =
  'https://cdn.builder.io/o/assets%2F5b8073f890b043be81574f96cfd1250b%2Fafe011812da146a5b2263196cb25f263?alt=media&token=c017cd87-0598-4af2-8afd-e9b5a3fba078&apiKey=5b8073f890b043be81574f96cfd1250b';
const VIDEO_SRC =
  'https://cdn.builder.io/o/assets%2F5b8073f890b043be81574f96cfd1250b%2F8b210c56974440649a0a78d4a3a0ddc5%2Fcompressed?apiKey=5b8073f890b043be81574f96cfd1250b&token=8b210c56974440649a0a78d4a3a0ddc5&alt=media&optimized=true';
 
export default component$(() => {
  const audioElementSignal = useSignal<HTMLAudioElement | undefined>();
  const audioPlayButtonSignal = useSignal<HTMLButtonElement | undefined>();
  const audioIsPlayingSignal = useSignal(false);
  const videoElementSignal = useSignal<HTMLAudioElement | undefined>();
  const videoPlayButtonSignal = useSignal<HTMLButtonElement | undefined>();
  const videoIsPlayingSignal = useSignal(false);
  const playsInlineSignal = useSignal(true);
  const location = useLocation();
 
  const videoPoster =
    location.url.origin + '/sample-media/qwik-koi-poster.jpg';
 
  useStylesScoped$(`
        segment {
          display: flex;
          flex-direction: column;
          align-items: center;
          text-align: center;
          width: 100%;
          padding: 20px;
          color: #1dacf2
        }
        .content {
          width: 60%;
          min-width: 250px;
        }
        button {
          padding: 20px;
          font-weight: bold;
          font-size: 1.2em;
          width: 100%;
          background: #1dacf2;
          color: white;
        }
        .checkbox-container {
          display: flex;
          align-items: center;
          justify-content: center;
        }
        .checkbox {
          width: 20px;
          height: 20px;
          margin-right: 8px;
        }
        .video-container {
          position: relative;
          width: 100%;
          height: 0;
          padding-bottom: calc(56.25% + 1px);
        }
        video {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          box-sizing: border-box;
          border: 1px solid gray;
        }
        `);
 
  useVisibleTask$(({ track }) => {
    track(() => audioPlayButtonSignal.value);
    track(() => audioElementSignal.value);
 
    const play = () =>
      audioIsPlayingSignal.value
        ? audioElementSignal.value?.pause()
        : audioElementSignal.value?.play();
 
    audioPlayButtonSignal.value?.removeEventListener('click', play);
    audioPlayButtonSignal.value?.addEventListener('click', play);
 
    return () =>
      audioPlayButtonSignal.value?.removeEventListener('click', play);
  });
 
  useVisibleTask$(({ track }) => {
    track(() => videoPlayButtonSignal.value);
    track(() => videoElementSignal.value);
 
    const play = () =>
      videoIsPlayingSignal.value
        ? videoElementSignal.value?.pause()
        : videoElementSignal.value?.play();
 
    videoPlayButtonSignal.value?.addEventListener('click', play);
    return () =>
      videoPlayButtonSignal.value?.removeEventListener('click', play);
  });
 
  return (
    <segment>
      <div class="content">
        <h1>Media Controller</h1>
        <h3>
          <i>with iOS Support</i>
        </h3>
        <br />
        <div class="video-container">
          <video
            ref={videoElementSignal}
            src={VIDEO_SRC}
            poster={videoPoster}
            playsInline={playsInlineSignal.value}
            onPlay$={() => (videoIsPlayingSignal.value = true)}
            onPause$={() => (videoIsPlayingSignal.value = false)}
            onEnded$={() => (videoIsPlayingSignal.value = false)}
          />
        </div>
        <audio
          ref={audioElementSignal}
          src={AUDIO_SRC}
          onPlay$={() => (audioIsPlayingSignal.value = true)}
          onPause$={() => (audioIsPlayingSignal.value = false)}
          onEnded$={() => (audioIsPlayingSignal.value = false)}
        />
        <br />
        <div class="checkbox-container">
          <input
            type="checkbox"
            id="playsInlineCheckbox"
            class="checkbox"
            checked={playsInlineSignal.value}
            onchange$={() => {
              videoElementSignal.value?.pause();
              playsInlineSignal.value = !playsInlineSignal.value;
            }}
          />
          <label for="playsInlineCheckbox">playsInline (iOS)</label>
        </div>
 
        <br />
        <button ref={videoPlayButtonSignal}>
          {videoIsPlayingSignal.value ? 'Pause' : 'Play'} Video
        </button>
        <br />
        <br />
        <button ref={audioPlayButtonSignal}>
          {audioIsPlayingSignal.value ? 'Pause' : 'Play'} Audio
        </button>
      </div>
    </segment>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
