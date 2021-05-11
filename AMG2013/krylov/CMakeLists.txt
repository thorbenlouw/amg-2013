set(KRYLOV_HEADERS
        all_krylov.h
        gmres.h
        krylov.h
        pcg.h
        HYPRE_MatvecFunctions.h)

set(KRYLOV_SRCS
        gmres.c
        HYPRE_gmres.c
        HYPRE_pcg.c
        pcg.c)


add_library(krylov ${KRYLOV_SRCS} ${KRYLOV_HEADERS})
set_target_properties(krylov PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(krylov PRIVATE .. ../utilities)