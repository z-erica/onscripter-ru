project(
  'onscripter-ru',
  ['cpp', 'c'],
  default_options: [
    'c_std=c18',
    'cpp_std=c++20',
    'warning_level=2',
  ],
  version: '3572',
)

if host_machine.system() == 'linux'
  add_global_arguments('-DLINUX', language: ['c', 'cpp'])
endif

add_global_arguments('-DPUBLIC_RELEASE', language: ['c', 'cpp'])

embed = executable('embed', 'Tools/embed/embed.c')
resources = custom_target(
  'resources',
  output: 'Resources.cpp',
  command: [
    embed,
    '@SOURCE_ROOT@/Resources/Images/breakup-cellforms.png',
    'breakup-cellforms.png',
    '@SOURCE_ROOT@/Resources/Images/icon.png',
    'icon.png',
    '@SOURCE_ROOT@/Resources/Shaders/alphaOutsideTextures.frag',
    'alphaOutsideTextures.frag',
    '@SOURCE_ROOT@/Resources/Shaders/blendByMask.frag',
    'blendByMask.frag',
    '@SOURCE_ROOT@/Resources/Shaders/blurH.frag',
    'blurH.frag',
    '@SOURCE_ROOT@/Resources/Shaders/blurV.frag',
    'blurV.frag',
    '@SOURCE_ROOT@/Resources/Shaders/breakup.frag',
    'breakup.frag',
    '@SOURCE_ROOT@/Resources/Shaders/colorModification.frag',
    'colorModification.frag',
    '@SOURCE_ROOT@/Resources/Shaders/colourConversion.frag',
    'colourConversion.frag',
    '@SOURCE_ROOT@/Resources/Shaders/cropByMask.frag',
    'cropByMask.frag',
    '@SOURCE_ROOT@/Resources/Shaders/defaultVertex.vert',
    'defaultVertex.vert',
    '@SOURCE_ROOT@/Resources/Shaders/effectTrvswave.frag',
    'effectTrvswave.frag',
    '@SOURCE_ROOT@/Resources/Shaders/effectWarp.frag',
    'effectWarp.frag',
    '@SOURCE_ROOT@/Resources/Shaders/effectWhirl.frag',
    'effectWhirl.frag',
    '@SOURCE_ROOT@/Resources/Shaders/glassSmash.frag',
    'glassSmash.frag',
    '@SOURCE_ROOT@/Resources/Shaders/glyphGradient.frag',
    'glyphGradient.frag',
    '@SOURCE_ROOT@/Resources/Shaders/mergeAlpha.frag',
    'mergeAlpha.frag',
    '@SOURCE_ROOT@/Resources/Shaders/multiplyAlpha.frag',
    'multiplyAlpha.frag',
    '@SOURCE_ROOT@/Resources/Shaders/pixelate.frag',
    'pixelate.frag',
    '@SOURCE_ROOT@/Resources/Shaders/renderSubtitles.frag',
    'renderSubtitles.frag',
    '@SOURCE_ROOT@/Resources/Shaders/textFade.frag',
    'textFade.frag',
    '@OUTPUT@',
  ],
)

sources = [
  'Engine/Components/Async.cpp',
  'Engine/Components/Dialogue.cpp',
  'Engine/Components/DynamicProperty.cpp',
  'Engine/Components/Fonts.cpp',
  'Engine/Components/GlyphAtlas.cpp',
  'Engine/Components/Joystick.cpp',
  'Engine/Components/TextWindow.cpp',
  'Engine/Components/Window.cpp',
  'Engine/Core/Animation.cpp',
  'Engine/Core/Command.cpp',
  'Engine/Core/CommandExt.cpp',
  'Engine/Core/Effect.cpp',
  'Engine/Core/EffectBreakup.cpp',
  'Engine/Core/EffectTrig.cpp',
  'Engine/Core/Event.cpp',
  'Engine/Core/File.cpp',
  'Engine/Core/Image.cpp',
  'Engine/Core/Lips.cpp',
  'Engine/Core/Loader.cpp',
  'Engine/Core/ONScripter.cpp',
  'Engine/Core/Parser.cpp',
  'Engine/Core/ParserCommand.cpp',
  'Engine/Core/Sound.cpp',
  'Engine/Core/Text.cpp',
  'Engine/Entities/Animation.cpp',
  'Engine/Entities/ConstantRefresh.cpp',
  'Engine/Entities/Font.cpp',
  'Engine/Entities/Glyph.cpp',
  'Engine/Entities/StringTree.cpp',
  'Engine/Graphics/Common.cpp',
  'Engine/Graphics/GL2.cpp',
  'Engine/Graphics/GLES2.cpp',
  'Engine/Graphics/GLES3.cpp',
  'Engine/Graphics/GPU.cpp',
  'Engine/Graphics/PNG.cpp',
  'Engine/Graphics/Pool.cpp',
  'Engine/Handlers/LUA.cpp',
  'Engine/Handlers/Script.cpp',
  'Engine/Layers/Furu.cpp',
  'Engine/Layers/Layer.cpp',
  'Engine/Layers/Media.cpp',
  'Engine/Layers/ObjectFall.cpp',
  'Engine/Layers/Subtitle.cpp',
  'Engine/Media/AudioDecoder.cpp',
  'Engine/Media/Controller.cpp',
  'Engine/Media/Demux.cpp',
  'Engine/Media/HardwareDecoder.cpp',
  'Engine/Media/SubtitleDecoder.cpp',
  'Engine/Media/SubtitleDriver.cpp',
  'Engine/Media/VideoDecoder.cpp',
  'Engine/Readers/Direct.cpp',
  'Engine/Readers/Nsa.cpp',
  'Engine/Readers/Sar.cpp',
  'External/ExceptionHandler.cpp',
  'External/slre.c',

  'Support/AudioBridge.cpp',
  'Support/Cache.cpp',
  'Support/DirPaths.cpp',
  'Support/DirtyRect.cpp',
  'Support/FileIO.cpp',
  'Support/Unicode.cpp',

  resources,
]

c = meson.get_compiler('c')

smpeg2 = c.find_library('smpeg2', has_headers: ['smpeg2/smpeg.h'])

sdl_gpu = static_library('sdl_gpu',
  [
    '3rdparty/sdl-gpu/src/SDL_gpu.c',
    '3rdparty/sdl-gpu/src/SDL_gpu_matrix.c',
    '3rdparty/sdl-gpu/src/SDL_gpu_renderer.c',
    '3rdparty/sdl-gpu/src/SDL_gpu_shapes.c',
    '3rdparty/sdl-gpu/src/externals/stb_image/stb_image.c',
    '3rdparty/sdl-gpu/src/externals/stb_image_write/stb_image_write.c',
    '3rdparty/sdl-gpu/src/renderer_GLES_1.c',
    '3rdparty/sdl-gpu/src/renderer_GLES_2.c',
    '3rdparty/sdl-gpu/src/renderer_GLES_3.c',
    '3rdparty/sdl-gpu/src/renderer_OpenGL_1.c',
    '3rdparty/sdl-gpu/src/renderer_OpenGL_1_BASE.c',
    '3rdparty/sdl-gpu/src/renderer_OpenGL_2.c',
    '3rdparty/sdl-gpu/src/renderer_OpenGL_3.c',
    '3rdparty/sdl-gpu/src/renderer_OpenGL_4.c',
  ],
  include_directories: [
    '3rdparty/sdl-gpu/include',
    '3rdparty/sdl-gpu/src/externals/stb_image',
    '3rdparty/sdl-gpu/src/externals/stb_image_write',
  ],
  c_args: ['-DSDL_GPU_DISABLE_GLES'],
  dependencies: [
    dependency('glew'),
    dependency('SDL2'),
  ])

libavcodec_dep = dependency('libavcodec',
  fallback: ['ffmpeg', 'libavcodec_dep'])

libavformat_dep = dependency('libavformat',
  fallback: ['ffmpeg', 'libavformat_dep'])

libavutil_dep = dependency('libavutil',
  fallback: ['ffmpeg', 'libavutil_dep'])

libswresample_dep = dependency('libswresample',
  fallback: ['ffmpeg', 'libswresample_dep'])

libswscale_dep = dependency('libswscale',
  fallback: ['ffmpeg', 'libswscale_dep'])

executable(
  'onscripter-ru',
  sources,
  dependencies: [
    dependency('libass'),
    libavcodec_dep,
    libavformat_dep,
    libavutil_dep,
    dependency('libpng'),
    libswresample_dep,
    libswscale_dep,
    dependency('libusb-1.0'),
    dependency('freetype2'),
    dependency('SDL2'),
    dependency('SDL2_image'),
    dependency('SDL2_mixer'),
    smpeg2,
    dependency('vorbisfile'),
    dependency('zlib'),
  ],
  include_directories: [
    '3rdparty/sdl-gpu/include',
  ],
  link_with: sdl_gpu,
  install: true,
)
