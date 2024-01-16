<template>
  <div class="flex">
    <aside class="hidden md:block w-56 bg-slate-600 h-screen">
      <div class="flex w-full justify-center bg-slate-700">
        <router-link :to="{ name: 'home' }" class="flex gap-2 p-4 items-center text-white">
          <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="#fafafa" viewBox="0 0 256 256">
            <path
              d="M223.68,66.15,135.68,18a15.88,15.88,0,0,0-15.36,0l-88,48.17a16,16,0,0,0-8.32,14v95.64a16,16,0,0,0,8.32,14l88,48.17a15.88,15.88,0,0,0,15.36,0l88-48.17a16,16,0,0,0,8.32-14V80.18A16,16,0,0,0,223.68,66.15ZM128,32l80.34,44-29.77,16.3-80.35-44ZM128,120,47.66,76l33.9-18.56,80.34,44ZM40,90l80,43.78v85.79L40,175.82Zm176,85.78h0l-80,43.79V133.82l32-17.51V152a8,8,0,0,0,16,0V107.55L216,90v85.77Z">
            </path>
          </svg>
          Dashboard
        </router-link>
      </div>
      <nav>
        <ul>
          <li>
            <router-link :to="{ name: 'home' }"
              class="flex gap-3 p-4 items-center text-slate-300 hover:bg-slate-500 hover:text-slate-200"
              aria-current="page">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 256 256">
                <path
                  d="M218.83,103.77l-80-75.48a1.14,1.14,0,0,1-.11-.11,16,16,0,0,0-21.53,0l-.11.11L37.17,103.77A16,16,0,0,0,32,115.55V208a16,16,0,0,0,16,16H96a16,16,0,0,0,16-16V160h32v48a16,16,0,0,0,16,16h48a16,16,0,0,0,16-16V115.55A16,16,0,0,0,218.83,103.77ZM208,208H160V160a16,16,0,0,0-16-16H112a16,16,0,0,0-16,16v48H48V115.55l.11-.1L128,40l79.9,75.43.11.1Z">
                </path>
              </svg>
              <span>Home</span>
            </router-link>
          </li>
          <li>
            <router-link :to="{ name: 'posts.index' }"
              class="flex gap-3 p-4 items-center text-slate-300 hover:bg-slate-500 hover:text-slate-200"
              aria-current="page">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="#fafafa" viewBox="0 0 256 256">
                <path
                  d="M88,96a8,8,0,0,1,8-8h64a8,8,0,0,1,0,16H96A8,8,0,0,1,88,96Zm8,40h64a8,8,0,0,0,0-16H96a8,8,0,0,0,0,16Zm32,16H96a8,8,0,0,0,0,16h32a8,8,0,0,0,0-16ZM224,48V156.69A15.86,15.86,0,0,1,219.31,168L168,219.31A15.86,15.86,0,0,1,156.69,224H48a16,16,0,0,1-16-16V48A16,16,0,0,1,48,32H208A16,16,0,0,1,224,48ZM48,208H152V160a8,8,0,0,1,8-8h48V48H48Zm120-40v28.7L196.69,168Z">
                </path>
              </svg>
              <span>Posts</span>
            </router-link>
          </li>
          <li>
            <router-link :to="{ name: 'users.index' }"
              class="flex gap-3 p-4 items-center text-slate-300 hover:bg-slate-500 hover:text-slate-200"
              aria-current="page">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="#fafafa" viewBox="0 0 256 256"><path d="M117.25,157.92a60,60,0,1,0-66.5,0A95.83,95.83,0,0,0,3.53,195.63a8,8,0,1,0,13.4,8.74,80,80,0,0,1,134.14,0,8,8,0,0,0,13.4-8.74A95.83,95.83,0,0,0,117.25,157.92ZM40,108a44,44,0,1,1,44,44A44.05,44.05,0,0,1,40,108Zm210.14,98.7a8,8,0,0,1-11.07-2.33A79.83,79.83,0,0,0,172,168a8,8,0,0,1,0-16,44,44,0,1,0-16.34-84.87,8,8,0,1,1-5.94-14.85,60,60,0,0,1,55.53,105.64,95.83,95.83,0,0,1,47.22,37.71A8,8,0,0,1,250.14,206.7Z"></path></svg>
              <span>Users</span>
            </router-link>
          </li>
        </ul>
      </nav>
    </aside>
    <main class="w-full">
      <div class="flex justify-between items-center p-5 bg-slate-100 text-slate-600 border-[1px] border-b-slate-300">
        <div class="flex gap-5">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 256 256">
            <path
              d="M224,128a8,8,0,0,1-8,8H40a8,8,0,0,1,0-16H216A8,8,0,0,1,224,128ZM40,72H216a8,8,0,0,0,0-16H40a8,8,0,0,0,0,16ZM216,184H40a8,8,0,0,0,0,16H216a8,8,0,0,0,0-16Z">
            </path>
          </svg>
        </div>
        <div class="flex gap-3 items-center">
          <ul class="hidden md:flex gap-2">
            <li>
              <a href="#">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 256 256">
                  <path
                    d="M221.8,175.94C216.25,166.38,208,139.33,208,104a80,80,0,1,0-160,0c0,35.34-8.26,62.38-13.81,71.94A16,16,0,0,0,48,200H88.81a40,40,0,0,0,78.38,0H208a16,16,0,0,0,13.8-24.06ZM128,216a24,24,0,0,1-22.62-16h45.24A24,24,0,0,1,128,216ZM48,184c7.7-13.24,16-43.92,16-80a64,64,0,1,1,128,0c0,36.05,8.28,66.73,16,80Z">
                  </path>
                </svg>
              </a>
            </li>
            <li>
              <a href="#">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 256 256">
                  <path
                    d="M80,64a8,8,0,0,1,8-8H216a8,8,0,0,1,0,16H88A8,8,0,0,1,80,64Zm136,56H88a8,8,0,0,0,0,16H216a8,8,0,0,0,0-16Zm0,64H88a8,8,0,0,0,0,16H216a8,8,0,0,0,0-16ZM44,52A12,12,0,1,0,56,64,12,12,0,0,0,44,52Zm0,64a12,12,0,1,0,12,12A12,12,0,0,0,44,116Zm0,64a12,12,0,1,0,12,12A12,12,0,0,0,44,180Z">
                  </path>
                </svg>
              </a>
            </li>
            <li>
              <a href="#">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 256 256">
                  <path
                    d="M228.44,89.34l-96-64a8,8,0,0,0-8.88,0l-96,64A8,8,0,0,0,24,96V200a16,16,0,0,0,16,16H216a16,16,0,0,0,16-16V96A8,8,0,0,0,228.44,89.34ZM96.72,152,40,192V111.53Zm16.37,8h29.82l56.63,40H56.46Zm46.19-8L216,111.53V192ZM128,41.61l81.91,54.61-67,47.78H113.11l-67-47.78Z">
                  </path>
              </svg>
            </a>
          </li>
        </ul>
        <div class="flex">
          <a href="#" class="flex gap-2 items-center">
            <img src="https://www.khafid.web.id/_next/image?url=%2Fimages%2Fkhafid.jpg&w=256&q=75" alt="avatar"
              class="w-8 h-8 rounded-full">
          </a>
        </div>
      </div>
    </div>
    <!--- render router view -->
    <router-view></router-view>
  </main>
</div></template>