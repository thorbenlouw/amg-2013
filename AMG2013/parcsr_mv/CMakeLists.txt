set(PARSCR_MV_HEADERS
        headers.h
        HYPRE_parcsr_mv.h
        new_commpkg.h
        par_csr_communication.h
        par_csr_matrix.h
        parcsr_mv.h
        par_vector.h)

set(PARSCR_MV_SRCS
        HYPRE_parcsr_matrix.c
        HYPRE_parcsr_vector.c
        new_commpkg.c
        par_csr_assumed_part.c
        par_csr_communication.c
        par_csr_matop.c
        par_csr_matrix.c
        par_csr_matop_marked.c
        par_csr_matvec.c
        par_vector.c)


add_library(parcsr_mv ${PARSCR_MV_SRCS} ${PARSCR_MV_HEADERS})
set_target_properties(parcsr_mv PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(parcsr_mv PRIVATE .. ../utilities ../seq_mv)