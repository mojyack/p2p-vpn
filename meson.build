project(
    'shortwire',
    'cpp',
    version: '1.0.0',
    default_options: ['warning_level=3', 'werror=false', 'cpp_std=c++23'],
)
add_project_arguments('-Wno-missing-field-initializers', language: 'cpp')
add_project_arguments('-Wfatal-errors', language: 'cpp')

subdir('src/plink')
subdir('src/p2p/net/discord')

executable(
    'shortwired',
    files(
        'src/args.cpp',
        'src/common.cpp',
        'src/crypto/aes.cpp',
        'src/p2p/conn.cpp',
        # 'src/crypto/cipher.cpp',   # included in plink
        # 'src/crypto/c20p1305.cpp', # included in plink
        'src/shortwired.cpp',
    ) + plink_client_files + netprotocol_discord_files,
    dependencies: [dependency('libjuice')] + plink_client_deps + crypto_utils_deps + netprotocol_discord_deps,
    install: true,
)

executable(
    'tun-test',
    files(
        'src/common.cpp',
        'src/tun-test.cpp',
    ),
)
