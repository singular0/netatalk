if build_xml_docs
    if get_option('with-manual') == 'www'
        input_file = 'html-www.xsl.in'
        python = find_program('python3', required: false)
        if python.found()
            run_command(python, 'generate_compile_docs.py')
        endif
    else
        input_file = 'html.xsl.in'
    endif

    manpages_stylesheet = configure_file(
        input: 'man.xsl.in',
        output: 'man.xsl',
        configuration: cdata,
    )

    manual_stylesheet = configure_file(
        input: input_file,
        output: 'html.xsl',
        configuration: cdata,
    )

    subdir('manpages')

    if get_option('with-manual') != 'man_only'
        subdir('manual')

        if 'ja' in get_option('with-manual-l10n')
            subdir('ja')
        endif
    endif
endif

if get_option('with-readmes')
    readmes = [
        'DEVELOPER',
    ]

    if have_appletalk
        readmes += [
            'README.AppleTalk',
        ]
    endif

    foreach file : readmes
        install_data(
            file,
            install_dir: datadir / 'doc/netatalk',
        )
    endforeach
endif
