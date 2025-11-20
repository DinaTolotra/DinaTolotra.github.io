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
    <Languages className="w-4 h-4 text-gray-600 flex-shrink-0" />
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

  <div className="min-h-screen bg-gray-50">
    <div className="max-w-7xl mx-auto p-6 md:p-8">
      <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <aside className="lg:col-span-1 space-y-6">
          <div className="bg-white rounded-lg shadow-md p-8">
            <div className="flex justify-center mb-6">
              <div className="w-32 h-32 rounded-full bg-slate-700 flex items-center justify-center">
                <span className="text-5xl font-light text-white">D</span>
              </div>
            </div>

            <h1 className="text-2xl font-bold text-center text-slate-800 mb-1">
              DINA RATSINJOMANANA
            </h1>
            <p className="text-center text-slate-600 text-lg mb-8">Tolotra</p>

            <div className="border-t border-gray-200 pt-6">
              <h2 className="text-sm font-bold text-slate-700 mb-4 tracking-wider">
                {{t.profile}}
              </h2>
              <p className="text-sm text-gray-600 leading-relaxed">
                {{t.profileText}}
              </p>
            </div>
          </div>

          <div className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-4 tracking-wider border-b border-gray-200 pb-2">
              {{t.contact}}
            </h2>
            <div className="space-y-3">
              <div className="flex items-start gap-3">
                <MapPin className="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <span className="text-sm text-gray-600">ISD 2015 3205 Soatsihadino</span>
              </div>
              <div className="flex items-start gap-3">
                <Mail className="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <a href="mailto:ratsinjomananatolotra@gmail.com" className="text-sm text-gray-600 hover:text-slate-700 break-all">
                  ratsinjomananatolotra@gmail.com
                </a>
              </div>
              <div className="flex items-start gap-3">
                <Phone className="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <span className="text-sm text-gray-600">038 35 293 56</span>
              </div>
              <div className="flex items-start gap-3">
                <Github className="w-4 h-4 text-slate-600 mt-1 flex-shrink-0" />
                <a href="https://github.com/DinaTolotra" target="_blank" rel="noopener noreferrer" className="text-sm text-gray-600 hover:text-slate-700">
                  DinaTolotra
                </a>
              </div>
            </div>
          </div>

          <div className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-4 tracking-wider border-b border-gray-200 pb-2">
              {{t.languages}}
            </h2>
            <div className="space-y-2">
              <p className="text-sm text-gray-600">{{t.languagesList.malagasy}}</p>
              <p className="text-sm text-gray-600">{{t.languagesList.french}}</p>
              <p className="text-sm text-gray-600">{{t.languagesList.english}}</p>
            </div>
          </div>

          <div className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-4 tracking-wider border-b border-gray-200 pb-2">
              {{t.interests}}
            </h2>
            <div className="space-y-3">
              <div>
                <p className="text-sm font-semibold text-slate-700 mb-1">{{t.physical}}</p>
                <p className="text-sm text-gray-600">{{t.basketball}}</p>
              </div>
              <div>
                <p className="text-sm font-semibold text-slate-700 mb-1">{{t.intellectual}}</p>
                <p className="text-sm text-gray-600">{{t.reading}}</p>
              </div>
            </div>
          </div>
        </aside>

        <main className="lg:col-span-2 space-y-6">
          <section className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.education}}
            </h2>
            <div className="space-y-4">
              <div>
                <p className="text-sm font-semibold text-slate-800">{{t.education1}}</p>
              </div>
              <div>
                <p className="text-sm font-semibold text-slate-800">{{t.education2}}</p>
              </div>
              <div>
                <p className="text-sm font-semibold text-slate-800">{{t.education3}}</p>
              </div>
            </div>
          </section>

          <section className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.certificates}}
            </h2>
            <div className="space-y-6">
              <div>
                <div className="flex justify-between items-start mb-2">
                  <div>
                    <p className="text-xs text-gray-500 mb-1">09/2024</p>
                    <p className="text-sm font-bold text-slate-800">{{t.cert1Title}}</p>
                    <p className="text-xs text-gray-600">ODC Fianarantsoa</p>
                  </div>
                </div>
                <ul className="list-disc list-inside space-y-1 ml-2">
                  <li className="text-sm text-gray-600">{{t.cert1Desc1}}</li>
                  <li className="text-sm text-gray-600">{{t.cert1Desc2}}</li>
                </ul>
              </div>

              <div>
                <div className="flex justify-between items-start mb-2">
                  <div>
                    <p className="text-xs text-gray-500 mb-1">09/2024</p>
                    <p className="text-sm font-bold text-slate-800">{{t.cert2Title}}</p>
                    <p className="text-xs text-gray-600">Kaggle</p>
                  </div>
                </div>
                <ul className="list-disc list-inside space-y-1 ml-2">
                  <li className="text-sm text-gray-600">{{t.cert2Desc1}}</li>
                  <li className="text-sm text-gray-600">{{t.cert2Desc2}}</li>
                </ul>
              </div>

              <div>
                <div className="flex justify-between items-start mb-2">
                  <div>
                    <p className="text-xs text-gray-500 mb-1">06/2024</p>
                    <p className="text-sm font-bold text-slate-800">{{t.cert3Title}}</p>
                    <p className="text-xs text-gray-600">CodinGame</p>
                  </div>
                </div>
                <ul className="list-disc list-inside ml-2">
                  <li className="text-sm text-gray-600">{{t.cert3Desc}}</li>
                </ul>
              </div>

              <div>
                <div className="flex justify-between items-start mb-2">
                  <div>
                    <p className="text-xs text-gray-500 mb-1">09/2024</p>
                    <p className="text-sm font-bold text-slate-800">{{t.cert4Title}}</p>
                    <p className="text-xs text-gray-600">HackerRank</p>
                  </div>
                </div>
                <ul className="list-disc list-inside ml-2">
                  <li className="text-sm text-gray-600">{{t.cert4Desc}}</li>
                </ul>
              </div>
            </div>
          </section>

          <section className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.projects}}
            </h2>
            <div className="space-y-6">
              <div>
                <div className="flex items-start gap-3 mb-2">
                  <Github className="w-5 h-5 text-slate-600 mt-1 flex-shrink-0" />
                  <div>
                    <p className="text-xs text-gray-500 mb-1">10/2024 - ENI</p>
                    <p className="text-sm font-bold text-slate-800">{{t.project1Title}}</p>
                    <p className="text-sm text-gray-600 mt-2">{{t.project1Desc}}</p>
                  </div>
                </div>
              </div>

              <div>
                <div className="flex items-start gap-3 mb-2">
                  <Github className="w-5 h-5 text-slate-600 mt-1 flex-shrink-0" />
                  <div>
                    <p className="text-xs text-gray-500 mb-1">04/2025 - ENI</p>
                    <p className="text-sm font-bold text-slate-800">{{t.project2Title}}</p>
                    <p className="text-sm text-gray-600 mt-2">{{t.project2Desc}}</p>
                  </div>
                </div>
              </div>
            </div>
          </section>

          <section className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-sm font-bold text-slate-700 mb-6 tracking-wider border-b-2 border-slate-700 pb-2 inline-block">
              {{t.skills}}
            </h2>
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <h3 className="text-sm font-bold text-slate-700 mb-3">{{t.languages}}</h3>
                <div className="space-y-2">
                  <div className="flex justify-between items-center">
                    <span className="text-sm text-gray-600">JavaScript</span>
                    <span className="text-xs text-gray-500">Bien</span>
                  </div>
                  <div className="flex justify-between items-center">
                    <span className="text-sm text-gray-600">&nbsp;</span>
                    <span className="text-xs text-gray-500">&nbsp;</span>
                  </div>
                  <div className="flex justify-between items-center">
                    <span className="text-sm text-gray-600">C</span>
                    <span className="text-xs text-gray-500">Très bien</span>
                  </div>
                </div>
              </div>

              <div>
                <h3 className="text-sm font-bold text-slate-700 mb-3">{{t.framework}}</h3>
                <div className="space-y-2">
                  <div className="flex justify-between items-center">
                    <span className="text-sm text-gray-600">Vue</span>
                    <span className="text-xs text-gray-500">Bien</span>
                  </div>
                  <div className="flex justify-between items-center">
                    <span className="text-sm text-gray-600">Express</span>
                    <span className="text-xs text-gray-500">Très bien</span>
                  </div>
                  <div className="flex justify-between items-center">
                    <span className="text-sm text-gray-600">Linux API</span>
                    <span className="text-xs text-gray-500">Très bien</span>
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
