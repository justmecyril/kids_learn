<template>
  <div class="home">
    <div class="grid text-gray-600 md:grid-cols-3 font-body">
      <!-- content wrapper -->
      <div class="md:flex md:justify-end md:cols-span-1">
        <nav class="text-right">
          <div class="flex items-center justify-between">
            <h1 class="p-4 font-bold uppercase border-b border-gray-100">
              <a href="/" class="hover:text-gray-700">Kids Learn</a>
            </h1>
            <div class="px-4 cursor-pointer md:hidden">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="w-6 h-6"
                id="burger"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M4 6h16M4 12h16M4 18h16"
                />
              </svg>
            </div>
          </div>
          <ul class="hidden mt-6 text-sm md:block">
            <li class="py-1 font-bold text-gray-700">
              <a
                href="#"
                class="flex justify-end px-4 border-r-4 border-primary"
              >
                <span>Home</span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="w-5 h-6 ml-2"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
                  />
                </svg>
              </a>
            </li>
          </ul>
        </nav>
      </div>
      <!-- end nav -->
      <main class="px-16 py-6 bg-gray-100 md:col-span-2">
        <header>
          <h2 class="text-6xl font-semibold text-gray-700">Learning videos</h2>
          <h3 class="text-2xl">For Kids</h3>
        </header>

        <div>
          <h4 class="pb-2 mt-12 font-bold border-b border-gray-200">Nursery</h4>

          <div class="grid gap-10 mt-8 lg:grid-cols-3">
            <!-- cards -->
            <div
              v-for="rhyme in nurseryRhymesLoaded"
              :key="rhyme.id"
              class="card hover:shadow-lg"
            >
              <img
                :src="rhyme.image"
                class="object-cover w-full h-32 sm:h-48"
              />

              <div class="m-4">
                <span class="font-bold">{{ rhyme.title }}</span>
                <span class="block text-sm text-gray-500">{{
                  rhyme.createdBy
                }}</span>
              </div>
              <div class="badge">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="inline-block w-5 h-6 mr-1"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
                  />
                </svg>
                <span>{{ rhyme.duration }}</span>
              </div>
              <div class="flex justify-end btn">
                <span><a :href="rhyme.url" target="_blank">Watch</a></span>
              </div>
            </div>
          </div>

          <div class="flex justify-center mt-6">
            <div
              @click="loadMore"
              class="transform bg-secondary-100 text-secondary-200 btn hover:scale-125"
            >
              Load more
            </div>
          </div>

          <h4 class="pb-2 mt-12 font-bold border-b border-gray-200">
            Kindergarten
          </h4>
          <div class="grid gap-10 mt-8 lg:grid-cols-3">
            <!-- cards -->
            <div
              v-for="rhyme in kindergatenRhymesLoaded"
              :key="rhyme.id"
              class="card hover:shadow-lg"
            >
              <img
                :src="rhyme.image"
                class="object-cover w-full h-32 sm:h-48"
              />
              <div class="m-4">
                <span class="font-bold">{{ rhyme.title }}</span>
                <span class="block text-sm text-gray-500">{{
                  rhyme.createdBy
                }}</span>
              </div>
              <div class="badge">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="inline-block w-5 h-6 mr-1"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
                  />
                </svg>
                <span>{{ rhyme.duration }}</span>
              </div>
              <div class="flex justify-end btn">
                <span><a :href="rhyme.url" target="_blank">Watch</a></span>
              </div>
            </div>
          </div>

          <div class="flex justify-center mt-6">
            <div
              @click="loadMore2"
              class="transform bg-secondary-100 text-secondary-200 btn hover:scale-125"
            >
              Load more
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import { computed } from "@vue/runtime-core";
export default {
  name: "Home",
  components: {},
  setup() {
    const nurseryRhymes = ref([
      {
        title: "Polly had a Dolly",
        createdBy: "Cocomelon",
        duration: "55mins",
        image: require("@/assets/images/nursery1.jpg"),
        url: "https://www.youtube.com/watch?v=4Ka0LiNdpuE&t=5s ",
        id: 1,
      },
      {
        title: "Bubbles Song",
        createdBy: "Little Angel",
        duration: "22mins",
        image: require("@/assets/images/nursery2.jpg"),
        url: "https://www.youtube.com/watch?v=L6TBvTW0cJ4.",
        id: 2,
      },
      {
        title: "Five Little Ducks",
        createdBy: "Little Baby Bum",
        duration: "74mins",
        image: require("@/assets/images/nursery3.jpg"),
        url: "https://www.youtube.com/watch?v=tFoUuFq3vHw ",
        id: 3,
      },
      {
        title: "Incy Wincy Spider",
        createdBy: "Toddler Fun Learning",
        duration: "28mins",
        image: require("@/assets/images/nursery4.jpg"),
        url: "https://www.youtube.com/watch?v=buE6l32rCHo",
        id: 4,
      },
      {
        title: "Bob the Train",
        createdBy: "Bob the Train",
        duration: "4mins",
        image: require("@/assets/images/nursery5.jpg"),
        url: "https://www.youtube.com/watch?v=er6yZerHkcQ&t=37s",
        id: 5,
      },
      {
        title: "38 Songs for children",
        createdBy: "Nursery Rhymes Tv",
        duration: "71mins",
        image: require("@/assets/images/nursery6.jpg"),
        url: "https://www.youtube.com/watch?v=ohNSaUqZFiU",
        id: 6,
      },
      {
        title: "Baby Shark Dance",
        createdBy: "Happy Kids",
        duration: "3mins",
        image: require("@/assets/images/nursery7.jpg"),
        url: "https://www.youtube.com/watch?v=T72AM-INNwI",
        id: 7,
      },
      {
        title: "Ponytail",
        createdBy: "Badanamu",
        duration: "2mins",
        image: require("@/assets/images/nursery8.jpg"),
        url: "https://www.youtube.com/watch?v=BDg6-v9V8lo.",
        id: 8,
      },
      {
        title: "Twinkle Twinkle Little Star ",
        createdBy: "Eli Kids",
        duration: "6mins",
        image: require("@/assets/images/nursery9.jpg"),
        url: "https://www.youtube.com/watch?v=bwPK2qg3slk.",
        id: 9,
      },
    ]);

    const kindergatenRhymes = ref([
      {
        title: "Learning Videos for Toddlers",
        createdBy: "Boey Bear",
        duration: "35mins",
        image: require("@/assets/images/kin1.jpg"),
        url: "https://www.youtube.com/watch?v=jYCkh4cwDgA.",
        id: 1,
      },
      {
        title: "Basic Math For Kids",
        createdBy: "KidsEduc",
        duration: "22mins",
        image: require("@/assets/images/kin2.jpg"),
        url: "https://www.youtube.com/watch?v=N0_TWQTrJ-k ",
        id: 2,
      },
      {
        title: "1 Hour of Kids Music",
        createdBy: "123ABCtv",
        duration: "60mins",
        image: require("@/assets/images/kin3.jpg"),
        url: "https://www.youtube.com/watch?v=YDelk-PmL3k",
        id: 3,
      },
      {
        title: "Phonics Song | Junior Squad Cartoons",
        createdBy: "Kids Tv",
        duration: "60mins",
        image: require("@/assets/images/kin4.jpg"),
        url: "https://www.youtube.com/watch?v=nKVTzzr7EVo",
        id: 4,
      },
      {
        title: "Preschool Reading Lessons- Letter Blending | Sight Words",
        createdBy: "Lotty Learns",
        duration: "80mins",
        image: require("@/assets/images/kin5.jpg"),
        url: "https://www.youtube.com/watch?v=ycPaP_aONjE&t=10s",
        id: 5,
      },
      {
        title:
          "Preschool Learning for Kids (Learn the ABC's, Colors, Feelings, & More!)",
        createdBy: "Learning Time Fun",
        duration: "45mins",
        image: require("@/assets/images/kin6.jpg"),
        url: "https://www.youtube.com/watch?v=BqxlRQFMgEI",
        id: 6,
      },
      {
        title: "Meet the Math Facts - Addition & Subtraction Level 1",
        createdBy: "Preschool Prep Company",
        duration: "60mins",
        image: require("@/assets/images/kin7.jpg"),
        url: "https://www.youtube.com/watch?v=8cR_1Qi-tP4",
        id: 7,
      },
      {
        title:
          "Basic Math Addition For Kids | Noodle Kidz Pre-K and Kindergarten Educational Video",
        createdBy: "Noodle Kidz",
        duration: "8mins",
        image: require("@/assets/images/kin8.jpg"),
        url: "https://www.youtube.com/watch?v=mjlsSYLLOSE.",
        id: 8,
      },
      {
        title:
          "Preschool Learning Videos for 3 Year Olds | Kids Learning Videos | Educational Videos For Kids",
        createdBy: "The Soft Roots",
        duration: "102mins",
        image: require("@/assets/images/kin9.jpg"),
        url: "https://www.youtube.com/watch?v=38XyBuC6KuM.",
        id: 9,
      },
    ]);

    const nurseryVideosToShow = ref(3);

    const loadMore = () => {
      if (nurseryVideosToShow.value > nurseryRhymes.value.length) return;
      nurseryVideosToShow.value = nurseryVideosToShow.value + 3;
    };

    const nurseryRhymesLoaded = computed(() => {
      return nurseryRhymes.value.slice(0, nurseryVideosToShow.value);
    });

    const kindergatenVideosToShow = ref(3);

    const loadMore2 = () => {
      if (kindergatenVideosToShow.value > kindergatenRhymes.value.length)
        return;
      kindergatenVideosToShow.value = kindergatenVideosToShow.value + 3;
    };

    const kindergatenRhymesLoaded = computed(() => {
      return kindergatenRhymes.value.slice(0, kindergatenVideosToShow.value);
    });

    return {
      loadMore,
      loadMore2,
      nurseryRhymesLoaded,
      kindergatenRhymesLoaded,
    };
  },
};
</script>
