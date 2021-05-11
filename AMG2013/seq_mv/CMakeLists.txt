set(SEQ_MV_HEADERS
        csr_matrix.h
        headers.h
        HYPRE_seq_mv.h
        seq_mv.h
        vector.h)

set(SEQ_MV_SRCS
        big_csr_matrix.c
        csr_matop.c
        csr_matrix.c
        csr_matvec.c
        genpart.c
        HYPRE_csr_matrix.c
        HYPRE_vector.c
        vector.c)


add_library(seq_mv ${SEQ_MV_SRCS} ${SEQ_MV_HEADERS})
set_target_properties(seq_mv PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(seq_mv PRIVATE .. ../utilities ../seq_mv)