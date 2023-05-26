# Copyright (c) 2012 CNRS
# Author: Florent Lamiraux
#
# This file is part of agimus_sot_msgs.
# agimus_sot_msgs is free software: you can redistribute it
# and/or modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation, either version
# 3 of the License, or (at your option) any later version.
#
# agimus_sot_msgs is distributed in the hope that it will be
# useful, but WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Lesser Public License for more details.  You should have
# received a copy of the GNU Lesser General Public License along with
# agimus_sot_msgs.  If not, see
# <http://www.gnu.org/licenses/>.

# Requires at least CMake 2.6 to configure the package.
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

set(PROJECT_NAME agimus_sot_msgs)
set(PROJECT_DESCRIPTION "Messages and services for the agimus_sot package")
set(PROJECT_URL "")
set(PROJECT_USE_CMAKE_EXPORT TRUE)
set(PROJECT_EXPORT_NO_TARGET TRUE)
set(INSTALL_DOCUMENTATION OFF)

include(cmake/base.cmake)

compute_project_args(PROJECT_ARGS LANGUAGES CXX)
project(${PROJECT_NAME} ${PROJECT_ARGS})

find_package(catkin REQUIRED COMPONENTS sensor_msgs geometry_msgs message_generation)

add_service_files(FILES
    SetJointNames.srv
    GetJointNames.srv
    SetString.srv
    PlugSot.srv
    GetInt.srv
    ReadQueue.srv
    GetBasePoseAtParam.srv
    # Still useful ?
    SetInt.srv
    SetPose.srv
    WaitForQueueRecData.srv
    SetQueueRecData.srv
  )

add_message_files(FILES
    PlanningGoal.msg
    ReadSubPath.msg
    ProblemSolved.msg)

generate_messages(DEPENDENCIES std_msgs sensor_msgs geometry_msgs)

catkin_package(DEPENDS message_runtime)
