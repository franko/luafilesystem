project('luafilesystem', 'c', version : '1.8.0', default_options : ['c_std=gnu99'])

lua_puc_rio_dep = dependency('lua', required : false)
if lua_puc_rio_dep.found()
    lua_dep = lua_puc_rio_dep
    # We get the first 3 characters because we don't want the minor
    # version number.
    lua_abiver = lua_dep.version().substring(0, 3)
else
    lua_dep = dependency('luajit')
    if lua_dep.version().substring(0, 3) in ['2.0', '2.1']
        lua_abiver = '5.1'
    else
        error('unknown luajit version: ' + lua_dep.version())
    endif
endif

lfs_include_dir = include_directories('src')

shared_library('lfs', 'src/lfs.c',
    dependencies : lua_dep,
    include_directories : lfs_include_dir,
    name_prefix : '',
    install_dir : 'lib/lua/' + lua_abiver,
    install : true,
)
