<template>
     <footer class="relative py-16 overflow-hidden bg-Grey">
      <div class="container px-4 mx-auto">
        <div class="flex flex-wrap items-center lg:gap-[162px] gap-4">
          <div class="w-full mb-8 md:w-auto md:mb-0">
            <NuxtImg src="/img/Logo2.svg" alt="Kore Agro Logo" class="w-auto h-[125px]" />
          </div>
          <div class="flex flex-wrap gap-8 lg:gap-16">
            <div>
              <h3 class="mb-4 font-semibold">Keresés</h3>
              <ul class="space-y-2">
                <li><a href="#" class="hover:text-primary">Részletes Kereső</a></li>
                <li><a href="#" class="hover:text-primary">Összes gép</a></li>
                <li><a href="#" class="hover:text-primary">Új gépek</a></li>
                <li><a href="#" class="hover:text-primary">Használt gépek</a></li>
              </ul>
            </div>
            <div>
              <h3 class="mb-4 font-semibold">Információk</h3>
              <ul class="space-y-2">
                <li><a href="#" class="hover:text-primary">Rólunk</a></li>
                <li><a href="#" class="hover:text-primary">Referenciák</a></li>
                <li><a href="#" class="hover:text-primary">Adatkezelési Tájékoztató</a></li>
                <li><a href="#" class="hover:text-primary">Blog</a></li>
              </ul>
            </div>
            <div>
              <h3 class="mb-4 font-semibold">Kapcsolat</h3>
              <ul class="space-y-2">
                <li class="flex items-center">
                  <PhosphorIconMapPin class="w-5 h-5 mr-2 text-primary" />
                  <span class="font-semibold">5200 Törökszentmiklós Surjány, Nyírfa út 3.</span>
                </li>
                <li class="flex items-center">
                  <PhosphorIconEnvelopeSimple class="w-5 h-5 mr-2 text-primary" />
                  <a href="mailto:korezsolt2@gmail.com" class="font-semibold hover:text-primary">korezsolt2@gmail.com</a>
                </li>
                <li class="flex items-center">
                  <PhosphorIconPhone class="w-5 h-5 mr-2 text-primary" />
                  <a href="tel:+36707755666" class="font-semibold hover:text-primary">+36 70 775 56 66</a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <NuxtImg src="/img/digital_seed.svg" alt="Digital Seed Studio" class="absolute bottom-0 right-0 h-[50px]" />
    </footer>
</template>