project(
  'MacOpenGLTesting',
  'c',
  meson_version : '>= 1.3.0',
  version : '0.1',
  default_options : ['warning_level=3', 'c_std=c17'],
)

cc = meson.get_compiler('c')

link_args = []
if host_machine.system() == 'darwin'
  link_args += [
    '-framework', 'OpenGL',
    '-framework', 'Cocoa',
    '-framework', 'IOKit',
    '-framework', 'CoreVideo'
  ]
endif

exe = executable(
  'main',
  ['src/main.c', 'src/glad.c', 'src/ui.c'],
  include_directories: include_directories('include'),
  dependencies : [
    cc.find_library('glfw3', dirs: [meson.project_source_root() / 'lib']),
  ],
  link_args: link_args,
  install : true,
)

test('basic', exe)
