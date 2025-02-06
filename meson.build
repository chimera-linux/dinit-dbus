project(
    'dinit-dbus',
    ['cpp'],
    version: '0.1',
    default_options: [
        'cpp_std=c++17',
        'warning_level=3',
        'buildtype=debugoptimized',
    ]
)

pfx = get_option('prefix')
datadir = get_option('datadir')

dbus = dependency('dbus-1', required: true)
libdinitctl = dependency('libdinitctl', required: true)

dbus_policy_dir = pfx / datadir / 'dbus-1/system.d'
dbus_system_srv_dir = dbus.get_pkgconfig_variable(
    'system_bus_services_dir',
    define_variable: ['datadir', pfx / datadir]
)
dbus_session_srv_dir = dbus.get_pkgconfig_variable(
    'session_bus_services_dir',
    define_variable: ['datadir', pfx / datadir]
)

executable(
    'dinit-dbus',
    'src/dinit-dbus.cc',
    install: true,
    dependencies: [dbus, libdinitctl],
)

install_data(
    'data/org.chimera.dinit.service',
    install_dir: dbus_session_srv_dir,
    install_mode: 'rw-r--r--'
)

install_data(
    'data/org.chimera.dinit.service',
    install_dir: dbus_system_srv_dir,
    install_mode: 'rw-r--r--'
)

install_data(
    'data/org.chimera.dinit.conf',
    install_dir: dbus_policy_dir,
    install_mode: 'rw-r--r--'
)
