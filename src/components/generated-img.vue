<template>
  <div class="image-rendered">
    <p>Save this image and use it!</p>
    <template v-if="data.template === 'tt'">
      <cld-image publicId="uniform-tt-bg" style="width: 800px">
        <cld-transformation width="1920" quality="auto" />

        <cld-transformation
          :overlay="{
            fontFamily: 'montserrat',
            fontSize: 40,
            fontWeight: 'bold',
            text: encodeURIComponent(data.subtitle),
          }"
          gravity="north_west"
          y="303"
          x="328"
          color="#FBA633"
          v-if="data.subtitle !== ''"
        />

        <cld-transformation
          :overlay="{
            fontFamily: 'montserrat',
            fontWeight: 'bold',
            fontSize: 100,
            text: encodeURIComponent(data.maintitle.toUpperCase()),
          }"
          gravity="north_west"
          y="371"
          x="328"
          color="#fff"
          crop="fit"
          width="1400"
          v-if="data.maintitle !== ''"
        />

        <cld-transformation
          v-if="data.dudes"
          overlay="uniform-tt-dudes"
          gravity="north_west"
          width="406"
          y="654"
          x="328"
        />
      </cld-image>
    </template>

    <template v-if="data.template === 'pm'">
      <cld-image publicId="uniform-pm-bg" style="width: 800px">
        <cld-transformation width="1920" quality="high" />

        <cld-transformation
          :overlay="{
            fontFamily: 'montserrat',
            fontSize: 40,
            fontWeight: 'bold',
            text: encodeURIComponent(data.subtitle),
          }"
          gravity="north_west"
          y="303"
          x="328"
          color="#FBA633"
          v-if="data.subtitle !== ''"
        />

        <cld-transformation
          :overlay="{
            fontFamily: 'montserrat',
            fontWeight: 'bold',
            fontSize: 100,
            text: encodeURIComponent(data.maintitle.toUpperCase()),
          }"
          gravity="north_west"
          y="371"
          x="328"
          color="#fff"
          crop="fit"
          width="1400"
          v-if="data.maintitle !== ''"
        />
      </cld-image>
    </template>
  </div>
</template>
<script>
export default {
  name: "GeneratedImg",
  props: {
    data: { type: Object, required: true },
  },
};
</script>
