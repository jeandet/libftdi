project(
  'libftdi1',
  'cpp','c',
  meson_version: '>= 0.64.0',
  version : '1.5' ,
  default_options : ['warning_level=3', 'cpp_std=c++17', 'default_library=static', 'buildtype=release'],
  license : 'GPL2'
)

libusb_dep = dependency('libusb-1.0')

lib_ftdi_inc = include_directories('src')

conf_data = configuration_data()
conf_data.set('MAJOR_VERSION', 1)
conf_data.set('MINOR_VERSION', 5)
conf_data.set('VERSION_STRING', '1.5')
conf_data.set('SNAPSHOT_VERSION', '')
configure_file(
  input : 'src/ftdi_version_i.h.in',
  output : 'ftdi_version_i.h',
  format : 'cmake@',
  configuration : {
    'MAJOR_VERSION' : 1,
    'MINOR_VERSION' : 5,
    'VERSION_STRING' : '1.5',
    'SNAPSHOT_VERSION' : '',
  }
)

libftdi = library('ftdi1', 'src/ftdi.c', 'src/ftdi_stream.c', include_directories: lib_ftdi_inc, dependencies:libusb_dep)

libftdi_dep = declare_dependency(include_directories:lib_ftdi_inc, link_with:libftdi)
