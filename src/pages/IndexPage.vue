<template>
  <q-page style="margin: 2rem 0 8rem 0">
    <header
      :class="
        $q.screen.lt.md
          ? 'flex items-center q-mr-lg'
          : 'flex items-center justify-around'
      "
    >
      <BookmarkLogo
        :style="$q.screen.lt.md ? 'margin-left: 2rem' : ''"
        :width="$q.screen.lt.md ? '160px' : '500px'"
      />
      <q-space v-if="$q.screen.lt.md"></q-space>
      <q-btn
        v-if="$q.screen.lt.md"
        @click="nav = true"
        size="sm"
        flat
        icon="img:images/icon-hamburger.svg"
      />
      <q-dialog
        style="background-color: hsl(229, 31%, 21%, 0.93)"
        v-model="nav"
        maximized
      >
        <div class="dialog column q-gutter-y-lg q-pt-md q-px-lg">
          <div class="flex">
            <BookmarkLogoMobile />
            <q-space></q-space>
            <q-btn icon="close" dense flat color="white" v-close-popup></q-btn>
          </div>
          <div class="column" style="font-family: 'Rubik-Regular', sans-serif">
            <q-separator color="positive" class="q-my-sm"></q-separator>
            <q-btn
              size="lg"
              :ripple="false"
              color="white"
              flat
              label="Features"
            ></q-btn>
            <q-separator color="positive" class="q-my-sm"></q-separator>
            <q-btn
              size="lg"
              :ripple="false"
              color="white"
              flat
              label="Pricing"
            ></q-btn>
            <q-separator color="positive" class="q-my-sm"></q-separator>
            <q-btn
              size="lg"
              :ripple="false"
              color="white"
              flat
              label="Contact"
            ></q-btn>
            <q-separator color="positive" class="q-my-sm"></q-separator>
            <q-btn
              size="lg"
              :ripple="false"
              color="white"
              class="q-mt-sm"
              style="font-family: 'Rubik-Medium', sans-serif"
              outline
              label="Login"
            ></q-btn>
          </div>
        </div>
      </q-dialog>
      <div v-if="!$q.screen.lt.md" class="q-gutter-x-lg" style="width: 561px">
        <q-btn class="nav-btn" flat label="Features"></q-btn>
        <q-btn class="nav-btn" flat label="Pricing"></q-btn>
        <q-btn class="nav-btn" flat label="Contact"></q-btn>
        <q-btn class="red-btn" unelevated label="Login"></q-btn>
      </div>
    </header>
    <div
      :class="$q.screen.lt.md ? 'column reverse' : 'flex justify-around'"
      style="margin-top: 5rem"
    >
      <div style="max-width: 450px">
        <h3
          :class="$q.screen.lt.md ? 'text-h4 text-center q-mb-lg ' : 'q-mb-lg'"
        >
          A Simple Bookmark Manager
        </h3>
        <p
          :class="$q.screen.lt.md ? 'text-center q-mx-lg' : ''"
          class="q-mb-lg"
        >
          A clean and simple interface to organize your favourite websites. Open
          a new browser tab and see your sites load instantly. Try it for free.
        </p>
        <div :class="$q.screen.lt.md ? 'flex flex-center' : ''">
          <q-btn class="google-btn" label="Get it on Chrome" no-caps></q-btn>
          <q-btn
            class="q-mx-md firefox-btn"
            label="Get it on Firefox"
            no-caps
          ></q-btn>
        </div>
      </div>
      <div class="tablet-container">
        <div class="background"></div>
        <q-img
          :width="$q.screen.lt.md ? '350px' : '600px'"
          src="images/illustration-hero.svg"
        ></q-img>
      </div>
    </div>
    <div class="column flex-center text-center q-mt-xl q-mb-lg">
      <h4 :class="$q.screen.lt.md ? 'text-h5 q-mb-md q-mt-xl' : 'q-mb-lg'">
        Features
      </h4>
      <p :class="$q.screen.lt.md ? 'q-mx-lg' : ''">
        Our aim is to make it quick and easy for you to access your favourite
        websites. Your bookmark sync between your devices so you can access them
        on the go.
      </p>
    </div>
    <div>
      <q-tabs
        :class="$q.screen.lt.md ? 'custom-indicator-tabs q-px-xl' : ''"
        v-model="activeTab"
        content-class="text-accent q-mb-xl"
        active-class="text-dark"
        indicator-color="secondary"
        align="center"
        narrow-indicator
        :vertical="$q.screen.lt.md ? true : false"
      >
        <q-separator></q-separator>
        <q-tab
          class="custom-tab"
          name="bookmarking"
          :ripple="false"
          no-caps
          label="Simple Bookmarking"
        />
        <q-separator></q-separator>
        <q-tab
          class="custom-tab"
          name="searching"
          :ripple="false"
          no-caps
          label="Speedy Searching"
        />
        <q-separator></q-separator>
        <q-tab
          class="custom-tab"
          name="sharing"
          :ripple="false"
          no-caps
          label="Easy Sharing"
        />
        <q-separator></q-separator>
      </q-tabs>
      <q-tab-panels v-model="activeTab" animated>
        <q-tab-panel v-for="(tab, index) in tabs" :key="index" :name="tab.name"
          ><div
            :class="$q.screen.lt.md ? 'column flex-center' : 'tab-container'"
          >
            <div
              :class="
                activeTab === 'bookmarking'
                  ? 'blue-background'
                  : 'blue-background-custom'
              "
            ></div>
            <q-img
              :src="tab.image"
              :width="$q.screen.lt.md ? '330px' : '600px'"
            ></q-img>

            <div
              :class="$q.screen.lt.md ? 'q-mt-lg text-center' : ''"
              style="max-width: 500px"
            >
              <h4 :class="$q.screen.lt.md ? 'q-mb-md text-h5' : 'q-mb-lg'">
                {{ tab.title }}
              </h4>
              <p :class="$q.screen.lt.md ? 'q-mx-md' : ''">
                {{ tab.content }}
              </p>
              <q-btn
                v-if="!$q.screen.lt.md"
                color="primary"
                class="q-px-md q-py-sm q-mt-sm"
                no-caps
                label="More Info"
              ></q-btn>
            </div>
          </div>
        </q-tab-panel>
      </q-tab-panels>
    </div>
    <div
      :class="$q.screen.lt.md ? 'q-mt-xl' : ''"
      class="column flex-center text-center"
    >
      <h4 :class="$q.screen.lt.md ? 'text-h5 q-mb-md ' : 'q-mb-lg'">
        Download the extension
      </h4>
      <p :class="$q.screen.lt.md ? 'q-mx-lg' : ''">
        We've got more browser in the pipeline. Please do let us know if you've
        got a favourite you'd like us to prioritize.
      </p>
    </div>
    <div
      :class="
        $q.screen.lt.md
          ? ' q-gutter-y-xl'
          : 'row flex-center q-pa-xl q-gutter-x-xl'
      "
      :style="$q.screen.lt.md ? 'padding: 15%' : 'height: 32rem'"
    >
      <div class="col-auto text-center self-start">
        <q-card>
          <q-img
            src="images/logo-chrome.svg"
            class="q-mt-lg"
            width="35%"
          ></q-img>
          <q-card-section>
            <h6 class="q-my-sm">Add to Chrome</h6>
            <p>Minimum version 62</p>
            <q-img src="images/bg-dots.svg" class="q-mb-md"></q-img>
            <q-btn
              no-caps
              class="text-caption q-px-lg q-py-sm"
              color="primary"
              label="Add & Install Extensions"
            ></q-btn>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-auto text-center self-center">
        <q-card>
          <q-img
            src="images/logo-firefox.svg"
            class="q-mt-lg"
            width="35%"
          ></q-img>
          <q-card-section>
            <h6 class="q-my-sm">Add to Firefox</h6>
            <p>Minimum version 55</p>
            <q-img src="images/bg-dots.svg" class="q-mb-md"></q-img>
            <q-btn
              no-caps
              class="text-caption q-px-lg q-py-sm"
              color="primary"
              label="Add & Install Extensions"
            ></q-btn>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-auto text-center self-end">
        <q-card>
          <q-img
            src="images/logo-opera.svg"
            class="q-mt-lg"
            width="35%"
          ></q-img>
          <q-card-section>
            <h6 class="q-my-sm">Add to Opera</h6>
            <p>Minimum version 46</p>
            <q-img src="images/bg-dots.svg" class="q-mb-md"></q-img>
            <q-btn
              no-caps
              class="text-caption q-px-lg q-py-sm"
              color="primary"
              label="Add & Install Extensions"
            ></q-btn>
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div class="column flex-center">
      <h4 :class="$q.screen.lt.md ? 'text-h5 q-px-xl text-center ' : ''">
        Frequently Asked Questions
      </h4>
      <p :class="$q.screen.lt.md ? 'text-center  q-px-lg' : 'text-center'">
        Here are some of our FAQs. If you have any other questions you'd like
        answered please feel free to email us.
      </p>
      <q-list
        :class="$q.screen.lt.md ? 'q-mt-lg q-px-lg' : 'q-mt-lg'"
        :style="$q.screen.lt.md ? '' : 'width: 500px'"
        separator
      >
        <q-separator></q-separator>
        <q-expansion-item
          v-for="(faq, index) in faqs"
          :key="index"
          v-model="isExpanded[index]"
          :label="faq.question"
          class="text-grey-7"
          header-class="text-dark"
          :expand-icon-class="iconClass(index)"
        >
          <div class="q-pa-md">{{ faq.answer }}</div>
        </q-expansion-item>
        <q-separator></q-separator>
      </q-list>
      <q-btn
        color="primary"
        class="q-px-md q-py-sm q-mt-xl"
        no-caps
        label="More Info"
      ></q-btn>
    </div>
  </q-page>
  <q-footer>
    <div
      class="text-caption text-center column flex-center q-mt-xl"
      style="letter-spacing: 4px; font-family: 'Rubik-Regular', sans-serif"
    >
      <span>35,000+ ALREADY JOINED</span>
      <h4
        :class="$q.screen.lt.md ? 'text-h5 q-px-lg q-mt-sm' : ''"
        :style="$q.screen.lt.md ? '' : 'max-width: 25%'"
      >
        Stay up-to-date with what we-re doing
      </h4>
      <q-form @submit.prevent="onSubmit">
        <div
          :class="
            $q.screen.lt.md
              ? 'column q-gutter-y-sm'
              : 'flex q-gutter-x-md items-start'
          "
        >
          <q-input
            v-model="email"
            outlined
            lazy-rules
            placeholder="Enter your email address"
            input-style="width:16rem"
            input-class="q-px-sm"
            bg-color="white"
            dense
            :rules="[emailRequired, validEmail]"
            :error="emailError"
          >
          </q-input>
          <q-btn
            type="submit"
            no-caps
            unelevated
            class="red-btn"
            style="padding: 0.44rem 2rem"
            label="Contact Us"
          ></q-btn>
        </div>
      </q-form>
    </div>
    <div
      :class="
        $q.screen.lt.md
          ? 'dark-footer column justify-evenly'
          : 'dark-footer flex justify-around'
      "
    >
      <div
        :class="
          $q.screen.lt.md
            ? 'column flex-center q-gutter-y-md '
            : 'flex q-gutter-x-xl'
        "
        :style="$q.screen.lt.md ? '' : 'width: 55%'"
      >
        <BookmarkLogoFooter />
        <div
          :class="$q.screen.lt.md ? 'column q-gutter-y-md' : 'q-gutter-x-lg'"
          style="font-family: 'Rubik-Regular', sans-serif"
        >
          <q-btn class="footer-btn" flat label="Features"></q-btn>
          <q-btn class="footer-btn" flat label="Pricing"></q-btn>
          <q-btn class="footer-btn" flat label="Contact"></q-btn>
        </div>
      </div>
      <div
        :class="
          $q.screen.lt.md
            ? 'flex flex-center q-gutter-x-lg q-mt-xl'
            : 'flex q-gutter-x-lg items-center'
        "
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24">
          <path
            class="icon"
            fill="#FFF"
            fill-rule="evenodd"
            d="M22.675 0H1.325C.593 0 0 .593 0 1.325v21.351C0 23.407.593 24 1.325 24H12.82v-9.294H9.692v-3.622h3.128V8.413c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12V24h6.116c.73 0 1.323-.593 1.323-1.325V1.325C24 .593 23.407 0 22.675 0z"
          />
        </svg>

        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="20">
          <path
            class="icon"
            fill="#FFF"
            fill-rule="evenodd"
            d="M24 2.557a9.83 9.83 0 0 1-2.828.775A4.932 4.932 0 0 0 23.337.608a9.864 9.864 0 0 1-3.127 1.195A4.916 4.916 0 0 0 16.616.248c-3.179 0-5.515 2.966-4.797 6.045A13.978 13.978 0 0 1 1.671 1.149a4.93 4.93 0 0 0 1.523 6.574 4.903 4.903 0 0 1-2.229-.616c-.054 2.281 1.581 4.415 3.949 4.89a4.935 4.935 0 0 1-2.224.084 4.928 4.928 0 0 0 4.6 3.419A9.9 9.9 0 0 1 0 17.54a13.94 13.94 0 0 0 7.548 2.212c9.142 0 14.307-7.721 13.995-14.646A10.025 10.025 0 0 0 24 2.557z"
          />
        </svg>
      </div>
    </div>
  </q-footer>
</template>

<script setup>
import { ref, computed } from "vue";
import BookmarkLogo from "components/BookmarkLogo.vue";
import BookmarkLogoFooter from "components/BookmarkLogoFooter.vue";
import BookmarkLogoMobile from "src/components/BookmarkLogoMobile.vue";

const activeTab = ref("bookmarking");
const email = ref("");
const emailError = ref(false);
const nav = ref(false);

const tabs = ref([
  {
    name: "bookmarking",
    label: "Simple Bookmarking",
    title: "Bookmark in one click",
    content:
      " Organize your bookmarks however you like. Our simple drag-and-drop interface gives you complete control over how you manage your favourite sites.",
    image: "images/illustration-features-tab-1.svg",
  },
  {
    name: "searching",
    label: "Speedy Searching",
    title: "Intelligent search",
    content:
      " Our powerful search feature will help you find saved sites in no time at all. No need to trawl through all of your bookmarks.",
    image: "images/illustration-features-tab-2.svg",
  },
  {
    name: "sharing",
    label: "Easy Sharing",
    title: "Share your bookmarks",
    content:
      " Easily share your bookmarks and collections with others. Create a shareable link that you can send at the click of a button.",
    image: "images/illustration-features-tab-3.svg",
  },
]);

const faqs = ref([
  {
    question: "What is Bookmark",
    answer:
      "Bookmark is a tool that helps you save and organize your favorite websites. It allows you to quickly and easily access them on your device.",
  },
  {
    question: "How can I request a new browser?",
    answer:
      "You can request a new browser by contacting our support team through the Help section.",
  },
  {
    question: "Is there a mobile app?",
    answer:
      "Yes, we offer a mobile app for both iOS and Android platforms for on-the-go access.",
  },
  {
    question: "What about other Chromium browsers?",
    answer:
      "Our extension works across all Chromium-based browsers, including Microsoft Edge and Brave.",
  },
]);
// Validation for email

const emailRequired = (val) => !!val || "Email is required";

const validEmail = (val) => {
  const pattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return pattern.test(val) || "Whoops, make sure it's an email";
};

const onSubmit = () => {
  if (!email.value) {
    emailError.value = true;
  } else if (!validEmail(email.value)) {
    emailError.value = true;
  } else {
    emailError.value = false;
    emailErrorMessage.value = "";
    console.log("Form submitted with email:", email.value);
  }
};

// Styling for expand icon

const isExpanded = ref(faqs.value.map(() => false));

const iconClass = (index) =>
  computed(() => (isExpanded.value[index] ? "text-secondary" : "text-primary"))
    .value;
</script>
