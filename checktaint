#!/bin/sh

# This script reads the /proc/sys/kernel/tainted file and determines the reason
# for kernel taint. Taint status messages sourced from 
# https://www.kernel.org/doc/html/latest/admin-guide/tainted-kernels.html

taint="$(cat /proc/sys/kernel/tainted)"
echo "Raw taint value: $taint"

if [ $taint -eq 0 ]; then
    echo "Kernel not tainted."

else
    echo "Kernel is tainted because:"
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Proprietary module was loaded."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Module was force loaded."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Kernel running on an out of specification system."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Module was force unloaded."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Processor reported a Machine Check Exception (MCE)."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Bad page referenced or some unexpected page flags."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Taint requested by userspace application."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Kernel died recently, i.e. there was an OOPS or BUG."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-ACPI table overridden by user."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Kernel issued warning."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Staging driver was loaded."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Workaround for bug in platform firmware applied."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Externally-built (“out-of-tree”) module was loaded."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Unsigned module was loaded."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Soft lockup occurred."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Kernel has been live patched."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Auxiliary taint, defined for and used by distros."
    fi
    taint=$((taint >> 1))
    if [ $((taint & 1)) -eq 1 ]; then
        echo "-Kernel was built with the struct randomization plugin."
    fi
fi

