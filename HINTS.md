Because we're using ASAN, we need to run this in a slightly different way, see docs/notes_for_asan.txt:

	sudo ~/afl-2.52b/experimental/asan_cgroups/limit_memory.sh -u fuzzer afl-fuzz -i in -o out -m none ./handshake

An alternative is to not use the limit_memory script, and instead pass `-m none` to afl-fuzz. This runs the risk of the target allocating a huge amount of memory, and Linux will then start killing processes underneath you.
