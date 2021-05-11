set(STRUCT_MV_HEADERS
        assumed_part.h
        box.h
        box_manager.h
        box_neighbors.h
        box_pthreads.h
        computation.h
        headers.h
        hypre_box_smp_forloop.h
        HYPRE_struct_mv.h
        struct_communication.h
        struct_grid.h
        struct_matrix.h
        struct_mv.h
        struct_stencil.h
        struct_vector.h)

set(STRUCT_MV_SRCS
        assumed_part.c
        box_algebra.c
        box_alloc.c
        box_boundary.c
        box.c
        box_manager.c
        box_neighbors.c
        communication_info.c
        computation.c
        grow.c
        HYPRE_struct_grid.c
        HYPRE_struct_matrix.c
        HYPRE_struct_stencil.c
        HYPRE_struct_vector.c
        new_assemble.c
        new_box_neighbors.c
        project.c
        struct_axpy.c
        struct_communication.c
        struct_copy.c
        struct_grid.c
        struct_innerprod.c
        struct_io.c
        struct_matrix.c
        struct_matrix_mask.c
        struct_matvec.c
        struct_overlap_innerprod.c
        struct_scale.c
        struct_stencil.c
        struct_vector.c)


add_library(struct_mv ${STRUCT_MV_SRCS} ${SSTRUCT_MV_HEADERS})
set_target_properties(struct_mv PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(struct_mv PRIVATE
        ../
        ../utilities
        )