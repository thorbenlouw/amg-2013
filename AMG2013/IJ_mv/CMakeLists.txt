set(IJ_HEADERS
        aux_parcsr_matrix.h
        aux_par_vector.h
        headers.h
        HYPRE_IJ_mv.h
        IJ_matrix.h
        IJ_mv.h
        IJ_vector.h)

set(IJ_SRCS
        aux_parcsr_matrix.c
        aux_par_vector.c
        HYPRE_IJMatrix.c
        HYPRE_IJVector.c
        IJMatrix.c
        IJMatrix_parcsr.c
        IJVector_parcsr.c)


add_library(libIJ_mv ${IJ_SRCS} ${IJ_HEADERS})
set_target_properties(libIJ_mv PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(libIJ_mv PRIVATE ../ ../utilities ../struct_mv ../seq_mv ../parcsr_mv ../parcsr_ls)