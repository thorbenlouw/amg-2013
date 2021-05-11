set(SSTRUCT_MV_HEADERS
        box_map.h
        headers.h
        HYPRE_sstruct_mv.h
        sstruct_graph.h
        sstruct_grid.h
        sstruct_matrix.h
        sstruct_mv.h
        sstruct_stencil.h
        sstruct_vector.h)

set(SSTRUCT_MV_SRCS
        box_map.c
        HYPRE_sstruct_graph.c
        HYPRE_sstruct_grid.c
        HYPRE_sstruct_matrix.c
        HYPRE_sstruct_stencil.c
        HYPRE_sstruct_vector.c
        sstruct_axpy.c
        sstruct_copy.c
        sstruct_graph.c
        sstruct_grid.c
        sstruct_innerprod.c
        sstruct_matrix.c
        sstruct_matvec.c
        sstruct_overlap_innerprod.c
        sstruct_scale.c
        sstruct_stencil.c
        sstruct_vector.c)


add_library(sstruct_mv ${SSTRUCT_MV_SRCS} ${SSTRUCT_MV_HEADERS})
set_target_properties(sstruct_mv PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(sstruct_mv PRIVATE
        ../
        ../utilities
        ../struct_mv
        ../seq_mv
        ../parcsr_mv
        ../IJ_mv)