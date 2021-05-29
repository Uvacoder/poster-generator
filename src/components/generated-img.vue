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
        <cld-transformation width="1920" quality="auto" />

        <cld-transformation
          v-for="person in people"
          :key="person.overlay"
          :overlay="person.overlay"
          gravity="north_west"
          width="250"
          y="415"
          :x="person.x"
        />

        <cld-transformation
          overlay="uniform-pm-logo"
          gravity="north_west"
          width="120"
          y="551"
          :x="people[0].x + 200"
          v-if="data.logo"
        />

        <cld-transformation
          :overlay="{
            fontFamily: 'montserrat',
            fontSize: 130,
            fontWeight: 'black',
            text: encodeURIComponent(data.maintitle),
          }"
          gravity="north_west"
          y="684"
          x="150"
          color="#ffffff"
          v-if="data.subtitle !== ''"
        />

        <cld-transformation
          :overlay="{
            fontFamily: 'montserrat',
            fontWeight: 'medium',
            fontSize: 60,
            text: encodeURIComponent(data.subtitle),
          }"
          gravity="north_west"
          y="862"
          x="150"
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

  computed: {
    people() {
      const result = this.data.people.map((person, index) => {
        return {
          overlay: person,
          x: index === 0 ? 150 : 150 + index * 200,
        };
      });

      return result.reverse();
    },
  },
};
</script>
