project('writeas-gtk', ['vala', 'c'],
    version: '1.0.2',
    license: 'GPL',
    meson_version: '>=0.46.0')

i18n = import('i18n')

build_platform = get_option('platform')
if build_platform == 'elementary'
  app_id = 'com.github.writeas.writeas-gtk'
else
  app_id = 'writeas-gtk'
endif

conf = configuration_data()
conf.set_quoted('GETTEXT_PACKAGE', app_id)
conf.set_quoted('APP_ID', app_id)
conf.set_quoted('BUILD_PLATFORM', build_platform)
config_h = configure_file(output: 'config.h', configuration: conf)
config_h_dir = include_directories('.')

run_target('build', command: 'meson/build-cli.sh')

subdir('data')
subdir('src')
subdir('fonts/lora')

meson.add_install_script('meson/post_install.py')

