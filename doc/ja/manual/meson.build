manual_xml = configure_file(
    input: 'manual.xml.in',
    output: 'manual.xml',
    configuration: cdata,
)

configure_file(
    input: 'pageheader.txt.in',
    output: 'pageheader.txt',
    configuration: cdata,
)

manual_pages = [
    'compile.xml',
    'configuration.xml',
    'gpl.xml',
    'install.xml',
    'intro.xml',
    'upgrade.xml',
]

if have_appletalk
    manual_pages += [
        'appletalk.xml',
    ]
endif

foreach page : manual_pages
    configure_file(
        input: page,
        output: page,
        configuration: cdata,
    )
endforeach

manual_html = [
        'ad.1.html',
        'afp_signature.conf.5.html',
        'afp_voluuid.conf.5.html',
        'afp.conf.5.html',
        'afpd.8.html',
        'afpldaptest.1.html',
        'afppasswd.1.html',
        'afpstats.1.html',
        'afptest.1.html',
        'addump.1.html',
        'asip-status.1.html',
        'atalk.4.html',
        'atalk_aton.3.html',
        'cnid_dbd.8.html',
        'cnid_metad.8.html',
        'compile.html',
        'configuration.html',
        'dbd.1.html',
        'example-toc.html',
        'extmap.conf.5.html',
        'gpl.html',
        'index.html',
        'installation.html',
        'intro.html',
        'macusers.1.html',
        'man-pages.html',
        'manual-index.html',
        'netatalk.8.html',
        'table-toc.html',
        'upgrade.html',
]

if have_appletalk
    manual_html += [
        'a2boot.8.html',
        'aecho.1.html',
        'appletalk.html',
        'atalkd.8.html',
        'atalkd.conf.5.html',
        'getzones.1.html',
        'macipgw.8.html',
        'nbp.1.html',
        'nbp_name.3.html',
        'pap.1.html',
        'papd.8.html',
        'papd.conf.5.html',
        'papstatus.8.html',
        'timelord.8.html',
    ]
endif

custom_target(
    'manual',
    output: manual_html,
    input: manual_xml,
    command: [
        xsltproc,
        '--stringparam', 'generate.consistent.ids',
        '1',
        '-o', meson.current_build_dir() / 'manual',
        manual_stylesheet_ja,
        '@INPUT@',
    ],
    install: true,
    install_dir: manual_install_path / 'ja',
)
