project('hello-rust-cli',
        'rust',
        version: '0.1.0',
        license: 'GPL-3.0-or-later',
        meson_version: '>= 0.59')

i18n = import('i18n')
gnome = import('gnome')

base_id = 'org.gnome.HelloRustCli'
application_id = base_id

major_version = '0'
pre_release_version = '1.0'

version = major_version
if pre_release_version != ''
  version += '.' + pre_release_version
endif
full_version = version

dependency('glib-2.0', version: '>= 2.72') # update when changing gtk version
dependency('gio-2.0', version: '>= 2.72') # always same version as glib
dependency('gtk4', version: '>= 4.10.0')
dependency(
  'libadwaita-1', version: '>= 1.4.0',
  fallback: ['libadwaita', 'libadwaita_dep'],
  default_options: ['tests=false', 'examples=false', 'vapi=false']
)

# Please keep these dependencies sorted.
dependency('gstreamer-1.0', version: '>= 1.20')
dependency('gstreamer-base-1.0', version: '>= 1.20')
dependency('gstreamer-pbutils-1.0', version: '>= 1.20')
dependency('gstreamer-play-1.0', version: '>= 1.20')
dependency('gstreamer-video-1.0', version: '>= 1.20')
dependency(
  'gtksourceview-5', version: '>= 5.0.0',
  fallback: ['gtksourceview', 'gtksource_dep'],
  default_options: ['gtk_doc=false', 'sysprof=false', 'gir=false', 'vapi=false', 'install_tests=false']
)
dependency('openssl', version: '>= 1.0.1')
dependency('shumate-1.0', version: '>= 1.0.0')
dependency('sqlite3', version: '>= 3.24.0')

# Linux-only dependencies
if build_machine.system() == 'linux'
  dependency('libpipewire-0.3', version: '>= 0.3.0')
  dependency('xdg-desktop-portal', version: '>= 1.14.1')
endif

glib_compile_resources = find_program('glib-compile-resources', required: true)
glib_compile_schemas = find_program('glib-compile-schemas', required: true)
desktop_file_validate = find_program('desktop-file-validate', required: false)
appstreamcli = find_program('appstreamcli', required: false)
cargo = find_program('cargo', required: true)
cargo_version = run_command(cargo, '--version', check: true).stdout().strip()
message(cargo_version)
rustc_version = run_command('rustc', '--version', check: true).stdout().strip()
message(rustc_version)

subdir('src')
