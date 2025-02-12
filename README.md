# SLURM-Job-Script-for-Running-LAMMPS-with-Intel-MPI-Description-
This SLURM job script is designed to run LAMMPS (Large-scale Atomic/Molecular Massively Parallel Simulator) on a high-performance computing (HPC) cluster using Intel MPI. It specifies resource allocations, job parameters, and execution instructions for efficient parallel computation.
Steps Involved:
SLURM Directives for Resource Allocation:

#SBATCH -N 1 → Requests 1 node for computation.
#SBATCH --ntasks-per-node=48 → Allocates 48 cores per node for parallel processing.
#SBATCH --time=06:50:20 → Sets a maximum runtime of 6 hours, 50 minutes, and 20 seconds.
#SBATCH --job-name=lammps → Assigns "lammps" as the job name.
#SBATCH --error=job.%J.err_node_48 → Saves error messages to a file named job.<job_id>.err_node_48.
#SBATCH --output=job.%J.out_node_48 → Redirects job output to job.<job_id>.out_node_48.
#SBATCH --partition=standard → Submits the job to the "standard" queue/partition.
Set Execution Directory:

cd $SLURM_SUBMIT_DIR → Ensures the job runs in the directory from which it was submitted.
Configure Intel MPI Environment:

export I_MPI_FABRICS=shm:dapl → Sets Intel MPI fabric for optimal performance on newer versions (2019+).
Execute LAMMPS Using MPI:

mpiexec.hydra -n $SLURM_NTASKS lammps.exe
Runs LAMMPS in parallel across the allocated cores using MPI.
