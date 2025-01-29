# Trix

## Attach a button to Trix's toolbar

```js
#trixInitialize(event) {
  const buttonHTML = `<button type="button" data-trix-action="gallery" class="trix-button trix-button--icon">${galleryButtonSVG}</button>`
  // const buttonHTML = `<a href="${mediaLibraryPath}" data-turbo-frame="${window.Avo.configuration.modal_frame_id}" class="trix-button trix-button--icon">${galleryButtonSVG}</a>`
  if (event.target.toolbarElement && event.target.toolbarElement.querySelector('.trix-button-group--file-tools')) {
    event.target.toolbarElement
      .querySelector('.trix-button-group--file-tools')
      .insertAdjacentHTML('beforeend', buttonHTML)
  }

  // vm is the controller instance
  const vm = this
  const gallery = {
    test() {
      return true
    },
    perform() {
      // `this` is the trix instance
      // we need to set the outlet_selector to the unique_id of the trix field controller based on `this`
      // `this` will probide the context at runtime, when the action is called, not when tris is initially set.
      // we send that to the servr so the media library controller knows which field is being used to delegate the attach event
      const controllerElement = this.editor.element.closest('[data-trix-field-target="controller"]')
      get(`${mediaLibraryPath}`, {
        query: {
          resource_name: vm.resourceNameValue,
          record_id: vm.resourceIdValue,
          controller_selector: controllerElement.dataset.trixFieldUniqueSelectorValue,
          controller_name: vm.identifier,
        },
        responseKind: 'turbo-stream',
      })
    },
  }
  // Add the gallery action to the editor
  Object.assign(this.editorTarget.editorController.actions, { gallery })
}
```
