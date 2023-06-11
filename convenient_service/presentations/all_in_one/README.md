
## Acknowledgments

This presentation is built using the tools listed below. Many kudos to their contributors.

- [reveal.js](https://revealjs.com).

- [panzoom](https://github.com/anvaka/panzoom).

- [Sticker.js](http://stickerjs.cmiscm.com).

- [Tippy.js](https://atomiks.github.io/tippyjs).

## FAQ

### How to develop locally?

- Run the following commands.

  ```bash
  cd ~/Projects/static_content/convenient_service/presentations/all_in_one/
  ```

  ```bash
  npm install && npm start
  ```

  ```bash
  open localhost:8000
  ```

### How was this presentation created?

- Created and navigated to [convenient_service/presentations](https://github.com/marian13/static_content/tree/main/convenient_service/presentations) directory.

  ```bash
  cd ~/Projects/static_content/
  ```

  ```bash
  mkdir -p convenient_service/presentations
  ```

  ```bash
  cd convenient_service/presentations/
  ```

- Followed [reveal.js](https://revealjs.com/) [Installation Full Setup](https://revealjs.com/installation/#full-setup) guide.

  ```bash
  git clone https://github.com/hakimel/reveal.js.git all_in_one
  ```

- Removed all extra files that are involved directly neither in the development nor in the production of the presentation.

  ```bash
  cd all_in_one/
  ```

  ```bash
  rm -rf .git/ .github/ LICENSE README.md demo.html examples/ test/
  ```

- Added the following entry to the [static_content/index.html](https://github.com/marian13/static_content/blob/main/index.html).

  ```html
  <li>
    <span>Presentations</span>
    <ul>
      <li>
        <span>
          <a href="./convenient_service/presentations/all_in_one/index.html">All-in-One Presentation</a>
        </span>
      </li>
    </ul>
  </li>
  ```
