<template>
  <div class="bg-white">
    <!-- Header -->
    <header v-if="showHeader" class="absolute inset-x-0 top-0 z-50">
      <!-- <div class="px-5 py-3 bg-teal-700 text-xs sm:text-sm md:text-base text-center">
        <a href="" class="flex justify-center text-white">
          <span>July နဲ့ August မှာ In-class ၊ Online-live-class တွေဖွင့်ဖို့ရှိပါမယ်နော်။</span>
          <ArrowLongRightIcon class="w-5" />
        </a>
      </div>  -->
      <nav
        class="mx-auto flex max-w-7xl items-center justify-between p-6 lg:px-8"
        aria-label="Global"
      >
        <div class="flex lg:flex-1">
          <router-link :to="{ name: 'home' }" class="-m-1.5 p-1.5">
            <span class="sr-only">Your Company</span>
            <p class="text-xl font-b old">Hornbill-Education</p>
          </router-link>
        </div>
        <div class="flex gap-6 lg:hidden">
          <div class="flex">
            <!-- <router-link :to="{ name: 'profile' }">
            <div class="tooltip tooltip-bottom" data-tip="Go to profile">
              <div class="avatar flex flex-col items-end">
                <div class="w-14 rounded-full cursor-pointer">
                  <img
                    src="https://daisyui.com/images/stock/photo-1534528741775-53994a69daeb.jpg"
                  />
                </div>
              </div>
            </div>
          </router-link> -->
            <div class="dropdown dropdown-end">
              <div tabindex="0">
                <div class="avatar flex flex-col items-center">
                  <div class="w-12 rounded-full cursor-pointer">
                    <img
                      src="https://daisyui.com/images/stock/photo-1534528741775-53994a69daeb.jpg"
                    />
                  </div>
                </div>
              </div>
              <ul
                tabindex="0"
                class="dropdown-content z-[1] menu p-2 shadow bg-base-100 rounded-box w-52 mt-2"
              >
                <li><router-link :to="{ name: 'profile' }">Profile</router-link></li>
                <li><a>Logout</a></li>
              </ul>
            </div>
          </div>
          <router-link
            :to="{ name: 'profileNotifications' }"
            class="noti-btn w-12 h-12 relative flex items-center justify-center rounded-full cursor-pointer border-0 transition duration-300"
          >
            <svg viewBox="0 0 448 512" class="bell w-6">
              <path
                d="M224 0c-17.7 0-32 14.3-32 32V49.9C119.5 61.4 64 124.2 64 200v33.4c0 45.4-15.5 89.5-43.8 124.9L5.3 377c-5.8 7.2-6.9 17.1-2.9 25.4S14.8 416 24 416H424c9.2 0 17.6-5.3 21.6-13.6s2.9-18.2-2.9-25.4l-14.9-18.6C399.5 322.9 384 278.8 384 233.4V200c0-75.8-55.5-138.6-128-150.1V32c0-17.7-14.3-32-32-32zm0 96h8c57.4 0 104 46.6 104 104v33.4c0 47.9 13.9 94.6 39.7 134.6H72.3C98.1 328 112 281.3 112 233.4V200c0-57.4 46.6-104 104-104h8zm64 352H224 160c0 17 6.7 33.3 18.7 45.3s28.3 18.7 45.3 18.7s33.3-6.7 45.3-18.7s18.7-28.3 18.7-45.3z"
              ></path>
            </svg>
            <span
              class="w-4 h-4 rounded-full bg-rose-500 text-white flex items-center justify-center text-xs absolute top-2 right-1.5"
              >1</span
            >
          </router-link>
          <div class="flex lg:hidden">
            <button
              type="button"
              class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700"
              @click="mobileMenuOpen = true"
            >
              <span class="sr-only">Open main menu</span>
              <Bars3Icon class="h-6 w-6" aria-hidden="true" />
            </button>
          </div>
        </div>
        <div class="hidden lg:flex lg:gap-x-12">
          <router-link
            v-for="item in navigation"
            :key="item.name"
            :to="{ name: item.href }"
            class="text-sm font-semibold leading-6 text-gray-900"
            >{{ item.name }}</router-link
          >
        </div>
        <div class="hidden lg:flex lg:flex-1 lg:justify-end">
          <router-link
            :to="{ name: 'login' }"
            class="text-sm font-semibold leading-6 text-gray-900"
            >Log in <span aria-hidden="true">&rarr;</span></router-link
          >
        </div>
      </nav>
      <Dialog
        as="div"
        class="lg:hidden"
        @close="mobileMenuOpen = false"
        :open="mobileMenuOpen"
      >
        <div class="fixed inset-0 z-50" />
        <DialogPanel
          class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10"
        >
          <div class="flex items-center justify-between">
            <a href="#" class="-m-1.5 p-1.5">
              <span class="sr-only">Your Company</span>
              <img
                class="h-8 w-auto"
                src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
                alt=""
              />
            </a>
            <button
              type="button"
              class="-m-2.5 rounded-md p-2.5 text-gray-700"
              @click="mobileMenuOpen = false"
            >
              <span class="sr-only">Close menu</span>
              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
            </button>
          </div>
          <div class="mt-6 flow-root">
            <div class="-my-6 divide-y divide-gray-500/10">
              <div class="space-y-2 py-6">
                <router-link
                  v-for="item in navigation"
                  :key="item.name"
                  :to="{ name: item.href }"
                  class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50"
                  >{{ item.name }}</router-link
                >
              </div>
              <div class="py-6">
                <router-link
                  :to="{ name: 'login' }"
                  class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50"
                  >Log in</router-link
                >
              </div>
            </div>
          </div>
        </DialogPanel>
      </Dialog>
    </header>
    <router-view v-slot="{ Component }">
      <transition name="route" mode="out-in">
        <component :is="Component"></component>
      </transition>
    </router-view>
    <!-- Footer -->
    <footer
      v-if="showFooter"
      class="mx-auto mt-32 max-w-7xl overflow-hidden px-6 pb-20 sm:pb-24 lg:px-8 relative"
    >
      <nav
        class="-mb-6 columns-2 sm:flex sm:justify-center sm:space-x-12"
        aria-label="Footer"
      >
        <div v-for="item in footerNavigation.main" :key="item.name" class="pb-6">
          <a
            :href="item.href"
            class="text-sm leading-6 text-gray-600 hover:text-gray-900"
            >{{ item.name }}</a
          >
        </div>
      </nav>
      <div class="mt-10 flex justify-center space-x-10">
        <a
          v-for="item in footerNavigation.social"
          :key="item.name"
          :href="item.href"
          class="text-gray-400 hover:text-gray-500"
        >
          <span class="sr-only">{{ item.name }}</span>
          <component :is="item.icon" class="h-6 w-6" aria-hidden="true" />
        </a>
      </div>
      <p class="mt-10 text-center text-xs leading-5 text-gray-500">
        &copy; 2020 Your Company, Inc. All rights reserved.
      </p>

      <transition name="btt-transition">
        <button
          v-show="backToTopVisible"
          @click="scrollToTop"
          class="btt w-11 h-11 bg-gradient-to-t from-cyan-400 to-blue-500 flex items-center justify-center rounded-full cursor-pointer border-0 shadow-cyan-500/50 fixed bottom-10 right-6"
        >
          <svg height="1.2em" class="arrow" viewBox="0 0 512 512">
            <path
              class="fill-white"
              d="M233.4 105.4c12.5-12.5 32.8-12.5 45.3 0l192 192c12.5 12.5 12.5 32.8 0 45.3s-32.8 12.5-45.3 0L256 173.3 86.6 342.6c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3l192-192z"
            ></path>
          </svg>
          <p
            class="text text-xs w-24 absolute -bottom-5 opacity-0 transition duration-700 text-gray-800 flex items-center justify-center"
          >
            Back to Top
          </p>
        </button>
      </transition>
    </footer>
  </div>
</template>

<script setup>
import { Dialog, DialogPanel } from "@headlessui/vue";
import { defineComponent, h, onMounted, onUnmounted, ref } from "vue";
import { Bars3Icon, XMarkIcon, ArrowLongRightIcon } from "@heroicons/vue/24/outline";
import { useRouter } from "vue-router";

const navigation = [
  { name: "Courses", href: "courses" },
  { name: "Roadmap", href: "roadmap" },
  { name: "Blogs", href: "blogs" },
  { name: "Gallery", href: "gallery" },
  { name: "Books", href: "books" },
  { name: "Mentorship", href: "mentorship" },
];

const footerNavigation = {
  main: [
    { name: "Blog", href: "#" },
    { name: "Jobs", href: "#" },
    { name: "Press", href: "#" },
    { name: "Accessibility", href: "#" },
    { name: "Partners", href: "#" },
  ],
  social: [
    {
      name: "Facebook",
      href: "#",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d:
                "M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
    {
      name: "Instagram",
      href: "#",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d:
                "M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
    {
      name: "Twitter",
      href: "#",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              d:
                "M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84",
            }),
          ]),
      }),
    },
    {
      name: "GitHub",
      href: "#",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d:
                "M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
    {
      name: "YouTube",
      href: "#",
      icon: defineComponent({
        render: () =>
          h("svg", { fill: "currentColor", viewBox: "0 0 24 24" }, [
            h("path", {
              "fill-rule": "evenodd",
              d:
                "M19.812 5.418c.861.23 1.538.907 1.768 1.768C21.998 8.746 22 12 22 12s0 3.255-.418 4.814a2.504 2.504 0 0 1-1.768 1.768c-1.56.419-7.814.419-7.814.419s-6.255 0-7.814-.419a2.505 2.505 0 0 1-1.768-1.768C2 15.255 2 12 2 12s0-3.255.417-4.814a2.507 2.507 0 0 1 1.768-1.768C5.744 5 11.998 5 11.998 5s6.255 0 7.814.418ZM15.194 12 10 15V9l5.194 3Z",
              "clip-rule": "evenodd",
            }),
          ]),
      }),
    },
  ],
};

const mobileMenuOpen = ref(false);

const showHeader = ref(true);
const showFooter = ref(true);

const router = useRouter();

router.beforeEach((to, from, next) => {
  // Check if the current route is "payment"
  if (to.name === "coursestream" || to.name === "studentPortfolio" || to.name === "quiz") {
    // Hide header and footer for payment route
    showHeader.value = false;
    showFooter.value = false;
    // console.log(showHeader);
  } else {
    // Show header and footer for other routes
    showHeader.value = true;
    showFooter.value = true;
    // console.log(showHeader);
  }
  next();
});

const menuVisible = ref(false);
const toggleMenu = () => {
  menuVisible.value = !menuVisible.value;
};

const backToTopVisible = ref(false);

const handleScroll = () => {
  backToTopVisible.value = window.scrollY > 800; // Show the button after scrolling 200px
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>
<style scoped>
.route-enter-from {
  opacity: 0;
  transform: translateY(100px);
}

.route-enter-active {
  transition: all 0.3s ease-out;
}

.route-leave-active {
  transition: all 0.3s ease-in;
}

.route-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}

.btt:hover .text {
  opacity: 1;
  transition-duration: 0.7s;
}

.btt:hover .arrow {
  animation: slide-in-bottom 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

@keyframes slide-in-bottom {
  0% {
    transform: translateY(10px);
    opacity: 0;
  }

  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.btt-transition-enter-active,
.btt-transition-leave-active {
  transition: opacity 0.5s;
}
.btt-transition-enter-from,
.btt-transition-leave-to {
  opacity: 0;
}
</style>
