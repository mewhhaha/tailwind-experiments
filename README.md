# Tailwind experiments

A list of experiments to make good looking components with Tailwind CSS. Some use buttons and the focus state to trigger an animation. But that trigger could be anything inside your program. Just an easy way to do it in the playground without including JavaScript.

## Flip card

https://play.tailwindcss.com/2MTLAR1Nqe

Use 3d transforms to flip the card. Focus the card to flip it.

Caveat I noticed is that putting overflow-hidden on the card itself causes issues.

```html
<div class="perspective-normal">
  <div
    tabindex="0"
    class="grid size-64 transition-transform duration-1000 transform-3d *:[grid-area:1/1] focus:rotate-y-180"
  >
    <div class="size-full bg-red-300 backface-hidden">Front</div>
    <div class="size-full rotate-y-180 bg-blue-300 backface-hidden">Back</div>
  </div>
</div>
```

## Tilting card

https://play.tailwindcss.com/QMwhtQgQxZ

This card uses a 3x3 area to tilt the card in different directions depending on where you hover.

```html
<div class="flex justify-center py-12">
  <div class="perspective-normal">
    <div
      class="size-64 origin-center transition-transform duration-300 ease-linear transform-3d has-[[data-col-1]:hover]:rotate-y-12 has-[[data-col-3]:hover]:-rotate-y-12 has-[[data-row-1]:hover]:-rotate-x-12 has-[[data-row-3]:hover]:rotate-x-12"
    >
      <div class="absolute inset-0 grid grid-cols-3">
        <div data-col-1 data-row-1></div>
        <div data-col-2 data-row-1></div>
        <div data-col-3 data-row-1></div>
        <div data-col-1 data-row-2></div>
        <div data-col-2 data-row-2></div>
        <div data-col-3 data-row-2></div>
        <div data-col-1 data-row-3></div>
        <div data-col-2 data-row-3></div>
        <div data-col-3 data-row-3></div>
      </div>
      <div
        class="size-full bg-gradient-to-r from-red-500 to-red-400 backface-hidden"
      >
        Front
      </div>
    </div>
  </div>
</div>
```

## Glossy card

https://play.tailwindcss.com/rvSB85shSp

This card uses a 3x3 area to move a centered affect to different areas of the card. Here it is a type of light effect that gets moved around.

```html
<div class="flex justify-center py-12">
  <div class="perspective-normal">
    <div class="size-64">
      <div class="absolute inset-0 grid grid-cols-3 overflow-hidden">
        <div data-col-1 data-row-1 class="peer"></div>
        <div data-col-2 data-row-1 class="peer"></div>
        <div data-col-3 data-row-1 class="peer"></div>
        <div data-col-1 data-row-2 class="peer"></div>
        <div data-col-2 data-row-2 class="peer"></div>
        <div data-col-3 data-row-2 class="peer"></div>
        <div data-col-1 data-row-3 class="peer"></div>
        <div data-col-2 data-row-3 class="peer"></div>
        <div data-col-3 data-row-3 class="peer"></div>
        <div
          class="pointer-events-none absolute inset-0 rounded-full bg-radial-[at_50%_50%] from-white to-gray-200 opacity-50 blur-3xl transition-transform duration-1000 ease-linear peer-[[data-col-1]:hover]:-translate-x-1/2 peer-[[data-col-3]:hover]:translate-x-1/2 peer-[[data-row-1]:hover]:-translate-y-1/2 peer-[[data-row-3]:hover]:translate-y-1/2"
        ></div>
      </div>
      <div
        class="size-full bg-gradient-to-r from-red-500 to-red-400 backface-hidden"
      >
        Front
      </div>
    </div>
  </div>
</div>
```

## Tilting glossy card

https://play.tailwindcss.com/LE4n5xeDXP

This is just a combination of the tilting card and the glossy card as they look good together.

```html
<div class="flex justify-center py-12">
  <div class="perspective-normal">
    <div
      class="size-64 origin-center transition-transform duration-300 ease-linear transform-3d has-[[data-col-1]:hover]:rotate-y-12 has-[[data-col-3]:hover]:-rotate-y-12 has-[[data-row-1]:hover]:-rotate-x-12 has-[[data-row-3]:hover]:rotate-x-12"
    >
      <div class="absolute inset-0 grid grid-cols-3 overflow-hidden">
        <div data-col-1 data-row-1 class="peer"></div>
        <div data-col-2 data-row-1 class="peer"></div>
        <div data-col-3 data-row-1 class="peer"></div>
        <div data-col-1 data-row-2 class="peer"></div>
        <div data-col-2 data-row-2 class="peer"></div>
        <div data-col-3 data-row-2 class="peer"></div>
        <div data-col-1 data-row-3 class="peer"></div>
        <div data-col-2 data-row-3 class="peer"></div>
        <div data-col-3 data-row-3 class="peer"></div>
        <div
          class="pointer-events-none absolute inset-0 rounded-full bg-radial-[at_50%_50%] from-white to-gray-200 opacity-50 blur-3xl transition-transform duration-1000 ease-linear peer-[[data-col-1]:hover]:-translate-x-1/2 peer-[[data-col-3]:hover]:translate-x-1/2 peer-[[data-row-1]:hover]:-translate-y-1/2 peer-[[data-row-3]:hover]:translate-y-1/2"
        ></div>
      </div>
      <div
        class="size-full bg-gradient-to-r from-red-500 to-red-400 backface-hidden"
      >
        Front
      </div>
    </div>
  </div>
</div>
```

## Entering card animation

https://play.tailwindcss.com/Xuun6WiOT9

This uses a list of cards stacked in a slightly tiled deck that will unravel on focus.

```html
<ul
  class="flex flex-row-reverse justify-end gap-2 duration-300 *:w-px *:transition-[width] focus-within:*:w-64"
  tabindex="0"
>
  <li class="perspective-normal">
    <div
      class="grid size-64 rotate-y-120 rotate-z-20 shadow-md transition-transform duration-200 transform-3d *:[grid-area:1/1] in-focus:rotate-y-0 in-focus:rotate-z-0"
    >
      <div class="size-full bg-red-300 backface-hidden">Front</div>
      <div class="size-full rotate-y-180 bg-blue-300 backface-hidden">Back</div>
    </div>
  </li>
  <li class="perspective-normal">
    <div
      class="grid size-64 rotate-y-120 rotate-z-20 shadow-md transition-transform duration-200 transform-3d *:[grid-area:1/1] in-focus:rotate-y-0 in-focus:rotate-z-0"
    >
      <div class="size-full bg-red-300 backface-hidden">Front</div>
      <div class="size-full rotate-y-180 bg-blue-300 backface-hidden">Back</div>
    </div>
  </li>
  <li class="perspective-normal">
    <div
      class="grid size-64 rotate-y-120 rotate-z-20 shadow-md transition-transform duration-200 transform-3d *:[grid-area:1/1] in-focus:rotate-y-0 in-focus:rotate-z-0"
    >
      <div class="size-full bg-red-300 backface-hidden">Front</div>
      <div class="size-full rotate-y-180 bg-blue-300 backface-hidden">Back</div>
    </div>
  </li>
</ul>
```
