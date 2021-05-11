set(PARCSR_LS_HEADERS
        aux_interp.h
        headers.h
        HYPRE_parcsr_ls.h
        par_amg.h
        parcsr_ls.h)

set(PARCSR_LS_SRCS
        aux_interp.c
        gen_redcs_mat.c
        HYPRE_parcsr_amg.c
        HYPRE_parcsr_gmres.c
        HYPRE_parcsr_pcg.c
        par_amg.c
        par_amg_setup.c
        par_amg_solve.c
        par_cg_relax_wt.c
        par_coarsen.c
        par_coarse_parms.c
        par_cycle.c
        par_indepset.c
        par_interp.c
        par_jacobi_interp.c
        par_multi_interp.c
        par_laplace_27pt.c
        par_laplace.c
        par_lr_interp.c
        par_nodal_systems.c
        par_rap.c
        par_rap_communication.c
        par_vardifconv.c
        par_relax.c
        par_relax_interface.c
        par_scaled_matnorm.c
        par_stats.c
        par_strength.c
        partial.c
        pcg_par.c
        par_relax_more.c)


add_library(parcsr_ls ${PARCSR_LS_SRCS} ${PARCSR_LS_HEADERS})
set_target_properties(parcsr_ls PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(parcsr_ls PRIVATE .. ../utilities ../krylov
        ../seq_mv
        ../parcsr_mv
        ../IJ_mv)