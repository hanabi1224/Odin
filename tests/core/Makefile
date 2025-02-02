ODIN=../../odin
PYTHON=$(shell which python3)
OUT_FILE=test_binary.bin

all: download_test_assets image_test compress_test strings_test hash_test crypto_test noise_test encoding_test \
	 math_test linalg_glsl_math_test filepath_test reflect_test os_exit_test

download_test_assets:
	$(PYTHON) download_assets.py

image_test:
	$(ODIN) run image/test_core_image.odin -out=$(OUT_FILE) -file

compress_test:
	$(ODIN) run compress/test_core_compress.odin -out=$(OUT_FILE) -file

strings_test:
	$(ODIN) run strings/test_core_strings.odin -out=$(OUT_FILE) -file

hash_test:
	$(ODIN) run hash -out=$(OUT_FILE) -o:speed -no-bounds-check

crypto_test:
	$(ODIN) run crypto -out=$(OUT_FILE) -o:speed -no-bounds-check

noise_test:
	$(ODIN) run math/noise -out=$(OUT_FILE)

encoding_test:
	$(ODIN) run encoding/hxa -out=$(OUT_FILE) -collection:tests=..
	$(ODIN) run encoding/json -out=$(OUT_FILE)
	$(ODIN) run encoding/varint -out=$(OUT_FILE)

math_test:
	$(ODIN) run math/test_core_math.odin -out=$(OUT_FILE) -file -collection:tests=..

linalg_glsl_math_test:
	$(ODIN) run math/linalg/glsl/test_linalg_glsl_math.odin -file -out=$(OUT_FILE) -collection:tests=..

filepath_test:
	$(ODIN) run path/filepath/test_core_filepath.odin -file -out=$(OUT_FILE) -collection:tests=..

reflect_test:
	$(ODIN) run reflect/test_core_reflect.odin -file -out=$(OUT_FILE) -collection:tests=..

os_exit_test:
	$(ODIN) run os/test_core_os_exit.odin -file -out=$(OUT_FILE) && exit 1 || exit 0
