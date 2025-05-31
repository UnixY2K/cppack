project(
    'CppPack',
    'cpp',
    default_options: ['cpp_std=c++17'],
    version: '1.0.0',
    license: 'MIT',
)

cpppack_incl = include_directories('msgpack/include')

cpppack_dep = declare_dependency(
    include_directories: cpppack_incl
)

if get_option('build_tests')
# catch2 for unit tests
catch2_with_main_dep = dependency(
                'catch2',
                fallback: ['catch2', 'catch2_with_main_dep']
)

test_sources = files(
    'msgpack/tests/error_handling.cpp',
    'msgpack/tests/examples.cpp',
    'msgpack/tests/main.cpp',
    'msgpack/tests/object_packing_tests.cpp',
    'msgpack/tests/type_packing_tests.cpp',
)

test_dependencies = [
    catch2_with_main_dep,
	cpppack_dep,
]

testexe = executable('testexe', test_sources,
                     dependencies: test_dependencies)

test('cpppack unit tests', testexe)
endif