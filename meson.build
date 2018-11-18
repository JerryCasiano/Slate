project('Slate')

sassc = find_program('sassc', required: false)

if sassc.found()

    sassc_opts = [ '-a', '-M', '-t', 'compact' ]

    scss_files = files([
      '_colors-public.scss',
      '_colors.scss',
      '_common.scss',
      '_drawing.scss',
      '_additions.scss',
    ])

    normal = custom_target('Slate',
                            input: 'gtk-contained.scss',
                            output: 'gtk.css',
                            command: [
                                sassc, sassc_opts, '@INPUT@', '@OUTPUT@',
                            ],
                            depend_files: scss_files,
                            build_by_default: true)

    variant = 'dark'

    dark = custom_target('Slate-' + variant,
                            input: 'gtk-contained-@0@.scss'.format(variant),
                            output: 'gtk-@0@.css'.format(variant),
                            command: [
                                sassc, sassc_opts, '@INPUT@', '@OUTPUT@',
                            ],
                            depend_files: scss_files,
                            build_by_default: true)

endif

theme_dir = join_paths(get_option('prefix'), get_option('datadir'), 'themes')
install_subdir('Slate', install_dir: theme_dir)
install_subdir('Slate-' + variant, install_dir: theme_dir)
