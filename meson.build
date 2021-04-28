project('luafilesystem', 'c', version: '0.7.1', default_options : ['c_std=gnu99', 'default_library=shared'])
# Do not use c99 for c standard as it will produce a wrong build because
# functions like localtime_r will be not declared and C will assume they
# return an integer instead of a pointer and on 64bit this is horribly
# wrong.
# The gnu99 standard ensure that __USE_POSIX is defined (among other
# things) to get declaration of functions like localtime_r.

lfs_include_dir = include_directories('src')

# Could be also Lua as well
lua_dep = dependency('luajit', required : true)

liblfs = shared_library('lfs',
    ['src/lfs.c'],
    dependencies: lua_dep,
    include_directories : lfs_include_dir,
    name_prefix: '',
    install_dir: 'bin',
    install: true
)

