# Galería (AOSP Gallery 2.3.6, branch `xt550-libre`)

This is the stock Android 2.3.6 2D Gallery (`android-2.3.6_r1`, commit `ea32625`,
Apache 2.0), built outside AOSP. It replaces Motorola's Gallery3D on a Motorola XT550.

## Changes

- Package `org.libregaleria`, no longer sharing the `android.media` uid
  (that needs the platform's media key).
- Removed unused permissions: camera, microphone, location, SMS.
- Handles `com.cooliris.media.action.REVIEW` for images and videos. The
  Motorola Camera uses that action to show the last photo or video taken.
- Uses public API instead of hidden members:
  - `getScrollX/Y()`, `getLeft()`… instead of `View.mScrollX/Y`, `mLeft`…;
  - `getContext()` instead of `mContext`;
  - `Theme.Dialog` instead of `Theme.Dialog.Alert`;
  - `android.R.drawable.ic_media_play` instead of the internal play icon.
- `inNativeAlloc` (hidden) is set by reflection, so thumbnails still count
  outside the Dalvik heap.
- Dropped the DRM image list (hidden `DrmStore` provider).
- The app label is "Galería".

## Tested on the XT550 (Android 2.3.6)

- Opens in Spanish.
- Views an image through the Camera's REVIEW action.
- Like the stock 2.3 Gallery, it lists only memory-card photos. The test phone has no
  card, so browsing albums still needs a card to be tested.
