<script setup>
import { ref } from 'vue'
import { Languages, MapPin, Mail, Phone, Github } from 'lucide-vue-next'
import { translations } from '@/assets/translation.js'

const languages = ref([
  { code: 'fr', label: 'FR', data: translations.fr },
  { code: 'en', label: 'EN', data: translations.en },
  { code: 'mg', label: 'MG', data: translations.mg }
]);

const currentLanguage = ref(languages.value[0]);
const t = ref(currentLanguage.value.data);
const isHovered = ref(false);

const onLanguageChange = (code) => {
  const lang = languages.value.find((elem) => {return elem.code === code;});
  currentLanguage.value = lang;
  t.value = lang.data;
}

</script>

<template>

  <div 
    class="group fixed top-6 right-6 z-50 flex items-center gap-2 bg-white shadow-lg rounded-lg p-2 overflow-hidden group w-12 hover:w-auto"
  >
    <Languages class="w-4 h-4 text-gray-600 flex-shrink-0" />
    <div 
      class="flex gap-1 opacity-0 w-0 group-hover:opacity-100 group-hover:w-auto"
    >
      <button
        v-for="lang in languages"
        :key="lang.code"
        @click="() => onLanguageChange(lang.code)"
        class="px-3 py-1 rounded text-sm font-medium text-gray-600 hover:bg-gray-100 whitespace-nowrap"
        :class="{'bg-slate-600 text-white': (currentLanguage.code === lang.code)}"
      >
        {{ lang.label }}
      </button>
    </div>
  </div>

  <div class="min-h-screen bg-gray-50">
    <div class="max-w-7xl mx-auto p-6 md:p-8">
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <aside class="lg:col-span-1 space-y-6">
          <div class="bg-white rounded-lg shadow-md p-8">
            <div class="flex justify-center mb-6">
              <div class="w-32 h-32 rounded-full bg-slate-700 flex items-center justify-center">
                <span class="text-5xl font-light text-white">D</span>
              </div>
            </div>

            <h1 class="text-2xl font-bold text-center text-slate-800 mb-1">
              DINA RATSINJOMANANA
            </h1>
            <p class="text-center text-slate-600 text-lg mb-8">Tolotra</p>

            <div class="border-t border-gray-200 pt-6">
              <h2 class="text-sm font-bold text-slate-700 mb-4 tracking-wider">
                {{t.profile}}
              </h2>
              <p class="text-sm text-gray-600 leading-relaxed">
                {{t.profileText}}
              </p>
            </div>
          </div>

          <div class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-4 tracking-wider border-b border-gray-200 pb-2">
              {{t.contact}}
            </h2>
            <div class="space-y-3">
              <div class="flex items-start gap-3">
                <MapPin class="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <span class="text-sm text-gray-600">ISD 2015 3205 Soatsihadino</span>
              </div>
              <div class="flex items-start gap-3">
                <Mail class="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <a href="mailto:ratsinjomananatolotra@gmail.com" class="text-sm text-gray-600 hover:text-slate-700 break-all">
                  ratsinjomananatolotra@gmail.com
                </a>
              </div>
              <div class="flex items-start gap-3">
                <Phone class="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <span class="text-sm text-gray-600">038 35 293 56</span>
              </div>
              <div class="flex items-start gap-3">
                <Github class="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <a href="https://github.com/DinaTolotra" target="_blank" rel="noopener noreferrer" class="text-sm text-gray-600 hover:text-slate-700">
                  DinaTolotra
                </a>
              </div>
            </div>
          </div>

          <div class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-4 tracking-wider border-b border-gray-200 pb-2">
              {{t.languages}}
            </h2>
            <div class="space-y-2">
              <p class="text-sm text-gray-600">{{t.languagesList.malagasy}}</p>
              <p class="text-sm text-gray-600">{{t.languagesList.french}}</p>
              <p class="text-sm text-gray-600">{{t.languagesList.english}}</p>
            </div>
          </div>

          <div class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-4 tracking-wider border-b border-gray-200 pb-2">
              {{t.interests}}
            </h2>
            <div class="space-y-3">
              <div>
                <p class="text-sm font-semibold text-slate-700 mb-1">{{t.physical}}</p>
                <p class="text-sm text-gray-600">{{t.basketball}}</p>
              </div>
              <div>
                <p class="text-sm font-semibold text-slate-700 mb-1">{{t.intellectual}}</p>
                <p class="text-sm text-gray-600">{{t.reading}}</p>
              </div>
            </div>
          </div>
        </aside>

        <main class="lg:col-span-2 space-y-6">
          <section class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.education}}
            </h2>
            <div class="space-y-4">
              <div>
                <p class="text-sm font-semibold text-slate-800">{{t.education1}}</p>
              </div>
              <div>
                <p class="text-sm font-semibold text-slate-800">{{t.education2}}</p>
              </div>
              <div>
                <p class="text-sm font-semibold text-slate-800">{{t.education3}}</p>
              </div>
            </div>
          </section>

          <section class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.certificates}}
            </h2>
            <div class="space-y-6">
              <div>
                <div class="flex justify-between items-start mb-2">
                  <div>
                    <p class="text-xs text-gray-500 mb-1">09/2024</p>
                    <p class="text-sm font-bold text-slate-800">{{t.cert1Title}}</p>
                    <p class="text-xs text-gray-600">ODC Fianarantsoa</p>
                  </div>
                </div>
                <ul class="list-disc list-inside space-y-1 ml-2">
                  <li class="text-sm text-gray-600">{{t.cert1Desc1}}</li>
                  <li class="text-sm text-gray-600">{{t.cert1Desc2}}</li>
                </ul>
              </div>

              <div>
                <div class="flex justify-between items-start mb-2">
                  <div>
                    <p class="text-xs text-gray-500 mb-1">09/2024</p>
                    <p class="text-sm font-bold text-slate-800">{{t.cert2Title}}</p>
                    <p class="text-xs text-gray-600">Kaggle</p>
                  </div>
                </div>
                <ul class="list-disc list-inside space-y-1 ml-2">
                  <li class="text-sm text-gray-600">{{t.cert2Desc1}}</li>
                  <li class="text-sm text-gray-600">{{t.cert2Desc2}}</li>
                </ul>
              </div>

              <div>
                <div class="flex justify-between items-start mb-2">
                  <div>
                    <p class="text-xs text-gray-500 mb-1">06/2024</p>
                    <p class="text-sm font-bold text-slate-800">{{t.cert3Title}}</p>
                    <p class="text-xs text-gray-600">CodinGame</p>
                  </div>
                </div>
                <ul class="list-disc list-inside ml-2">
                  <li class="text-sm text-gray-600">{{t.cert3Desc}}</li>
                </ul>
              </div>

              <div>
                <div class="flex justify-between items-start mb-2">
                  <div>
                    <p class="text-xs text-gray-500 mb-1">09/2024</p>
                    <p class="text-sm font-bold text-slate-800">{{t.cert4Title}}</p>
                    <p class="text-xs text-gray-600">HackerRank</p>
                  </div>
                </div>
                <ul class="list-disc list-inside ml-2">
                  <li class="text-sm text-gray-600">{{t.cert4Desc}}</li>
                </ul>
              </div>
            </div>
          </section>

          <section class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.projects}}
            </h2>
            <div class="space-y-6">
              <div>
                <div class="flex items-start gap-3 mb-2">
                  <Github class="w-5 h-5 text-slate-600 mt-1 flex-shrink-0" />
                  <div>
                    <p class="text-xs text-gray-500 mb-1">10/2024 - ENI</p>
                    <p class="text-sm font-bold text-slate-800">{{t.project1Title}}</p>
                    <p class="text-sm text-gray-600 mt-2">{{t.project1Desc}}</p>
                  </div>
                </div>
              </div>

              <div>
                <div class="flex items-start gap-3 mb-2">
                  <Github class="w-5 h-5 text-slate-600 mt-1 flex-shrink-0" />
                  <div>
                    <p class="text-xs text-gray-500 mb-1">04/2025 - ENI</p>
                    <p class="text-sm font-bold text-slate-800">{{t.project2Title}}</p>
                    <p class="text-sm text-gray-600 mt-2">{{t.project2Desc}}</p>
                  </div>
                </div>
              </div>
            </div>
          </section>

          <section class="bg-white rounded-lg shadow-md p-6">
            <h2 class="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.skills}}
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <h3 class="text-sm font-bold text-slate-700 mb-3">{{t.languages}}</h3>
                <div class="space-y-2">
                  <div class="flex justify-between items-center">
                    <span class="text-sm text-gray-600">C</span>
                    <span class="text-xs text-gray-500">Très bien</span>
                  </div>
                  <div class="flex justify-between items-center">
                    <span class="text-sm text-gray-600">JavaScript</span>
                    <span class="text-xs text-gray-500">Bien</span>
                  </div>
                </div>
              </div>

              <div>
                <h3 class="text-sm font-bold text-slate-700 mb-3">{{t.framework}}</h3>
                <div class="space-y-2">
                  <div class="flex justify-between items-center">
                    <span class="text-sm text-gray-600">Linux API</span>
                    <span class="text-xs text-gray-500">Très bien</span>
                  </div>
                  <div class="flex justify-between items-center">
                    <span class="text-sm text-gray-600">Vue</span>
                    <span class="text-xs text-gray-500">Bien</span>
                  </div>
                  <div class="flex justify-between items-center">
                    <span class="text-sm text-gray-600">Express</span>
                    <span class="text-xs text-gray-500">Très bien</span>
                  </div>
                </div>
              </div>
            </div>
          </section>
        </main>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
