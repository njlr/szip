genrule(
  name = 'configure',
  out = 'out',
  srcs = [
    'configure',
    'Makefile.in',
    'src/SZconfig.h.in',
    'src/Makefile.in',
    'src/rice.h',
    'bin/install-sh',
    'bin/missing',
    'bin/config.guess',
    'bin/config.sub',
    'examples/Makefile.in',
    'test/Makefile.in',
  ],
  cmd = 'cp -r $SRCDIR $OUT && cd $OUT && ./configure',
)

genrule(
  name = 'SZconfig.h',
  out = 'SZconfig.h', 
  cmd = 'cp $(location :configure)/src/SZconfig.h $OUT'
)

cxx_library(
  name = 'szip',
  header_namespace = '',
  exported_headers = {
    'szip/szlib.h': 'src/szlib.h',
    'szip/rice.h': 'src/rice.h',
    'szip/ricehdf.h': 'src/ricehdf.h',
    'szip/szip_adpt.h': 'src/szip_adpt.h',
  },
  headers = {
    'SZconfig.h': ':SZconfig.h',
  },
  srcs = glob([
    'src/*.c',
  ]),
  visibility = [
    'PUBLIC',
  ],
)

# cxx_library(
#   name = 'mcgill', 
#   exported_headers = {
#     'mcgill.h': 'test/mcgill.h',
#   },
#   srcs = [
#     'test/mcgill.c',
#   ],
# )

# cxx_binary(
#   name = 'example',
#   srcs = [
#     'examples/example.c',
#   ],
#   deps = [
#     ':szip',
#     ':mcgill',
#   ],
# )

# cxx_binary(
#   name = 'burst_szip',
#   srcs = [
#     'examples/burst_szip.c',
#   ],
#   deps = [
#     ':szip',
#     ':mcgill',
#   ],
# )
