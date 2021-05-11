set(UTILITIES_HEADERS
        amg_linklist.h
        exchange_data.h
        general.h
        hypre_memory.h
        hypre_smp_forloop.h
        HYPRE_utilities.h
        mpistubs.h
        threading.h
        thread_mpistubs.h
        timing.h
        umalloc_local.h
        utilities.h)

set(UTILITIES_SRCS
        amg_linklist.c
        binsearch.c
        exchange_data.c
        hypre_memory.c
        hypre_qsort.c
        memory_dmalloc.c
        mpistubs.c
        qsplit.c
        random.c
        threading.c
        thread_mpistubs.c
        timer.c
        timing.c
        umalloc_local.c
        hypre_error.c)

set_source_files_properties(timer.c PROPERTIES COMPILE_FLAGS "-D_POSIX_SOURCE -DHYPRE_TIMING")

add_library(libHYPRE_utilities ${UTILITIES_SRCS} ${UTILITIES_HEADERS} )
set_target_properties(libHYPRE_utilities  PROPERTIES LINKER_LANGUAGE CXX)
set_target_properties(libHYPRE_utilities PROPERTIES COMPILE_FLAGS "-DHYPRE_TIMING")
target_link_libraries(libHYPRE_utilities PUBLIC OpenMP::OpenMP_CXX)
target_include_directories(libHYPRE_utilities PRIVATE ../ OpenMP::OpenMP_INCLUDE)
