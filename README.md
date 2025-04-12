# frontendassignment
import axios from 'axios';

const BASE_URL = 'https://regres.in';

export const loginUser = async (credentials) => {
  try {
    const response = await axios.post(`${BASE_URL}/api/login`, credentials);
    return response.data;
  } catch (error) {
    throw new Error('Login failed. Please try again.');
  }
};

export const fetchUsers = async (page = 1) => {
  try {
    const response = await axios.get(`${BASE_URL}/api/users`, { params: { page } });
    return response.data;
  } catch (error) {
    throw new Error('Fetching users failed.');
  }
};

export const updateUser = async (id, data) => {
  try {
    const response = await axios.put(`${BASE_URL}/api/users/${id}`, data);
    return response.data;
  } catch (error) {
    throw new Error('Update failed.');
  }
};

export const deleteUser = async (id) => {
  try {
    const response = await axios.delete(`${BASE_URL}/api/users/${id}`);
    return response.data;
  } catch (error) {
    throw new Error('Delete failed.');
  }
};
