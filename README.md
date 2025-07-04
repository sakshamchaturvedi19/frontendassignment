// api.js
import axios from 'axios';

const BASE_URL = 'https://reqres.in/api';

/**
 * Logs in a user with given credentials.
 * @param {Object} credentials - { email, password }
 * @returns {Promise<Object>} - Response data with token
 */
export const loginUser = async (credentials) => {
  try {
    const response = await axios.post(`${BASE_URL}/login`, credentials);
    return response.data;
  } catch (error) {
    throw new Error(
      error.response?.data?.error || 'Login failed. Please try again.'
    );
  }
};

/**
 * Fetch users with pagination
 * @param {number} page - Page number
 * @returns {Promise<Object>} - Users data
 */
export const fetchUsers = async (page = 1) => {
  try {
    const response = await axios.get(`${BASE_URL}/users`, {
      params: { page },
    });
    return response.data;
  } catch (error) {
    throw new Error('Fetching users failed. Please try again.');
  }
};

/**
 * Update a user's data
 * @param {number|string} id - User ID
 * @param {Object} data - Data to update
 * @returns {Promise<Object>} - Updated user data
 */
export const updateUser = async (id, data) => {
  try {
    const response = await axios.put(`${BASE_URL}/users/${id}`, data);
    return response.data;
  } catch (error) {
    throw new Error('Update failed. Please try again.');
  }
};

/**
 * Delete a user by ID
 * @param {number|string} id - User ID
 * @returns {Promise<Object>} - Deletion status
 */
export const deleteUser = async (id) => {
  try {
    const response = await axios.delete(`${BASE_URL}/users/${id}`);
    return response.data;
  } catch (error) {
    throw new Error('Delete failed. Please try again.');
  }

}; 













import { loginUser, fetchUsers, updateUser, deleteUser } from './api';

// example usage
await loginUser({ email: 'eve.holt@reqres.in', password: 'cityslicka' });

