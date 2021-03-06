<template>
  <article
    class="cms-block-image-text-gallery"
    :style="{ backgroundColor: getBgColor }"
  >
    <div class="cms-block-image-text-gallery__container">
      <div class="cms-block-image-text-gallery__container__column">
        <CmsElementImage
          :content="getLeftColumn.image"
          @click.native="onImageClick(getLeftColumn)"
          v-bind:style="{ cursor: getLeftColumn.url && 'pointer' }"
        />
        <CmsElementText
          :content="getLeftColumn.text"
          class="cms-block-image-text-gallery__container__column--text"
        />
      </div>
      <div class="cms-block-image-text-gallery__container__column">
        <CmsElementImage
          :content="getCenterColumn.image"
          @click.native="onImageClick(getCenterColumn)"
          v-bind:style="{ cursor: getCenterColumn.url && 'pointer' }"
        />
        <CmsElementText
          :content="getCenterColumn.text"
          class="cms-block-image-text-gallery__container__column--text"
        />
      </div>
      <div class="cms-block-image-text-gallery__container__column">
        <CmsElementImage
          :content="getRightColumn.image"
          @click.native="onImageClick(getRightColumn)"
          v-bind:style="{ cursor: getRightColumn.url && 'pointer' }"
        />
        <CmsElementText
          :content="getRightColumn.text"
          class="cms-block-image-text-gallery__container__column--text"
        />
      </div>
    </div>
  </article>
</template>

<script>
import CmsGenericElement from "sw-cms/CmsGenericElement"
import CmsElementImage from "@shopware-pwa/default-theme/cms/elements/CmsElementImage"
import CmsElementText from "@shopware-pwa/default-theme/cms/elements/CmsElementText"

const extractGalleryData = (slots, position) => {
  const image = slots.find((slot) => slot.slot === `${position}-image`)
  const text = slots.find((slot) => slot.slot === `${position}-text`)
  const { newTab, url } = image && image.data
  return {
    image,
    text,
    url,
    newTab,
  }
}

export default {
  name: "CmsBlockImageTextGallery",
  components: {
    CmsGenericElement,
    CmsElementImage,
    CmsElementText,
  },
  props: {
    content: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    getBgColor() {
      return this.content.backgroundColor
    },
    getSlots() {
      return this.content.slots || []
    },
    getLeftColumn() {
      return extractGalleryData(this.getSlots, "left")
    },
    getCenterColumn() {
      return extractGalleryData(this.getSlots, "center")
    },
    getRightColumn() {
      return extractGalleryData(this.getSlots, "right")
    },
  },
  methods: {
    onImageClick(columnData) {
      if (columnData && columnData.url) {
        if (columnData.newTab) {
          window.open(columnData.url)
        } else {
          window.location.href = columnData.url
        }
      }
    },
  },
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/variables";

.cms-block-image-text-gallery {
  &__container {
    display: flex;
    flex-wrap: wrap;

    @include for-desktop {
      margin-right: 7rem;
      margin-left: 7rem;
    }
    &__column {
      padding: var(--spacer-sm);

      @include for-desktop {
        flex-grow: 1;
        flex: 1 1 0;
      }

      .cms-element-image {
        img {
          @include for-desktop {
            height: 320px;
            object-fit: cover;
          }
        }
      }

      &--text {
        text-align: center;
      }
    }
  }
}
</style>
