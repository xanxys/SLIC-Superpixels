# default header
import distutils.sysconfig
import os

env = Environment(
#	CXX = compiler,
	CXXFLAGS = '-std=c++11 -Wno-deprecated -Wno-attributes -shared -fPIC -DPIC',
	CCFLAGS = ['-O3', '-g'],
	CPPPATH = [
	distutils.sysconfig.get_python_inc(),
	],
	LIBPATH = [
	],
	CPPDEFINES = [
		# 'ENABLE_USB_IO'
	]
	)
env['ENV']['TERM'] = os.environ['TERM']

# project specific code
LIBS = [
	'libboost_system-mt',
	'libboost_thread-mt',
	'libdl',
	'libjsoncpp',
	'boost_python',
	'libopencv_core',
	'libopencv_highgui',
	'libopencv_imgproc',
	'libpthread',
]

# Magic to make .so compilation work
# from http://stackoverflow.com/questions/2246399/scons-to-make-a-shared-library-so-with-a-static-libarary-a
env['STATIC_AND_SHARED_OBJECTS_ARE_THE_SAME']=1
env.SharedLibrary(
	env.File('slic.so'),
	source =
		[env.Object(f) for f in env.Glob('*.cpp')],
	LIBS = LIBS)
