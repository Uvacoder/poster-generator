<template>
  <cld-image publicId="tt-bg" style="width: 800px">
    <cld-transformation width="1920" quality="auto" />

    <cld-transformation
      :overlay="{
        fontFamily: 'montserrat',
        fontSize: 40,
        fontWeight: 'bold',
        text: subtitle,
      }"
      gravity="north_west"
      y="303"
      x="328"
      color="#FBA633"
      v-if="subtitle !== ''"
    />

    <cld-transformation
      :overlay="{
        fontFamily: 'montserrat',
        fontWeight: 'bold',
        fontSize: 100,
        text: maintitle.toUpperCase(),
      }"
      gravity="north_west"
      y="371"
      x="328"
      color="#fff"
      crop="fit"
      width="1400"
      v-if="maintitle !== ''"
    />

    <cld-transformation
      v-if="dudes"
      overlay="dudes"
      gravity="north_west"
      width="406"
      y="654"
      x="328"
    />
  </cld-image>
</template>
<script>
export default {
  name: "GeneratedImg",
  props: {
    subtitle: { type: String },
    maintitle: { type: String },
    dudes: { type: Boolean },
  },
};
</script>
